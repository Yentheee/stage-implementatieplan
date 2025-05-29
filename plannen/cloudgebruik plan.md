# cloud-discorvery
### Defender for Endpoint
1. Ga naar https://security.microsoft.com/
2. Ga naar Cloud apps > Cloud Discovery
3. hier kun je dan alles zien van welke apps er gebruik gemaakt wordt en hoe vaak deze gebruikt worden op de apparaten die in Defender for Endpoint zitten.

---

#### Sophos 
1. Ga naar https://security.microsoft.com/
2. Ga naar Cloud apps > Cloud Discovery
3. Ga dan naar Actions en kies creat new Cloud Discovery report
4. Hier kun je dan de logs van de Sophos Firewall uploaden en zo kun je alle apps die gebruikt worden in kaart brengen.

---


### app-governance
1. Ga naar https://security.microsoft.com/appgovernance
2. Hier zie je een overzicht van de apps die toegang hebben tot de Microsoft 365-omgeving.
- Je kan hier de toegangrechten van de apps beheren.

---

### Conditional-access
1. Ga naar https://entra.microsoft.com
2. Ga naar Protection > Conditional access
3. Maak een nieuwe policy aan
- Je kan hier de policy zo inrichten dat het voldoet aan de eisen die je hebt. Dit kan bijvoorbeeld zijn dat je MFA moet gebruiken of dat je alleen toegang krijgt als je op een bepaalde locatie bent.

---

### data-loss-prevention
1. Ga naar https://purview.microsoft.com
2. Ga naar Data loss prevention > Policy
3. Hier kun je dan een policy aanmaken voor de verschillende locaties zoals Sharepoint, OneDrive en Exchange.
4. Maak een nieuwe rule aan. Gebruik bij Condition de optie Content contains sensitive info types en kies dan de gevoelige informatie die je wilt beschermen. (je kan sensitive info types ook zelf aanmaken)
5. Bij Action kies je de actie die je wilt uitvoeren als er gevoelige informatie gevonden wordt. Dit kan bijvoorbeeld zijn dat je een melding krijgt of dat de gebruiker een waarschuwing krijgt. Of blokkeer de actie.
6. Activeer de policy.

---

#### Script
```powershell
# --- Stap 1: Installeer en importeer benodigde module ---

if (-not (Get-Module -ListAvailable -Name ExchangeOnlineManagement)) {
    Install-Module -Name ExchangeOnlineManagement -Force -AllowClobber
}

Import-Module ExchangeOnlineManagement

# --- Stap 2: Verbinden met Security & Compliance PowerShell ---

$UserCredential = Get-Credential -Message "Vul je admin account in (bijv. admin@jouwdomein.com)"
Connect-IPPSSession -Credential $UserCredential

# --- Stap 3: Definieer policy en regel namen ---

$policyName = "Protect Sensitive Info - Credit Card"
$ruleName = "Block Credit Card Info Access"

try {
    # --- Stap 4: Controleren of de policy al bestaat ---
    $existingPolicy = Get-DlpCompliancePolicy -Identity $policyName -ErrorAction SilentlyContinue
    
    if ($null -eq $existingPolicy) {
        Write-Host "Policy bestaat niet, wordt aangemaakt..."
        New-DlpCompliancePolicy -Name $policyName -Mode Enable -Comment "Blokkeer creditcard info en waarschuw gebruiker"
        Write-Host "Policy aangemaakt."
    }
    else {
        Write-Host "Policy bestaat al."
    }

    # --- Stap 5: Controleren of de regel al bestaat ---
    $existingRule = Get-DlpComplianceRule -Policy $policyName -ErrorAction SilentlyContinue | Where-Object { $_.Name -eq $ruleName }

    if ($null -eq $existingRule) {
        Write-Host "Regel bestaat niet, wordt aangemaakt..."
        New-DlpComplianceRule -Name $ruleName -Policy $policyName `
            -ContentContainsSensitiveInformation @(@{Name="Credit Card Number"}) `
            -BlockAccess $true `
            -NotifyUser "Owner"
        Write-Host "Regel aangemaakt."
    }
    else {
        Write-Host "Regel bestaat al."
    }
}
catch {
    Write-Error "Fout bij aanmaken policy of regel: $_"
}

# --- Stap 6: Verbinding verbreken ---

Disconnect-ExchangeOnline -Confirm:$false

Write-Host "Script voltooid.
```
Als je dit script uitvoert in PowerShell, wordt er automatisch een DLP policy aangemaakt die creditcard informatie blokkeert en de gebruiker waarschuwt. Je kunt hier de parameters aanpassen/toevoegen naar wens.

---

#### Testen
Om dit te testen of het goed is toegepast ga je naar https://purview.microsoft.com en ga je naar Data loss prevention > Policy. Hier zie je de policy die je hebt aangemaakt.

Je kan ook dit script uitvoeren om te kijken of de policy goed is aangemaakt.
```powershell
Import-Module ExchangeOnlineManagement

$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential

$policyName = "Protect Sensitive Info - Credit Card"
$ruleName = "Block Credit Card Info Access"

$policy = Get-DlpCompliancePolicy -Identity $policyName -ErrorAction SilentlyContinue
if ($policy) {
    Write-Host "Policy '$policyName' bestaat."
    $rule = Get-DlpComplianceRule -Policy $policyName | Where-Object { $_.Name -eq $ruleName }
    if ($rule) {
        Write-Host "Regel '$ruleName' bestaat."
    } else {
        Write-Host "Regel '$ruleName' bestaat niet."
    }
} else {
    Write-Host "Policy '$policyName' bestaat niet."
}

Disconnect-ExchangeOnline -Confirm:$false
```
Pas de naam aan naar de naam die je hebt gegeven aan de policy en regel. Dit script controleert of de policy en regel bestaan en geeft een melding weer.

---

### real-time-scanning
1. Ga naar https://security.microsoft.com
2. Ga naar Cloud apps > Policies > Policy management
3. Maak een nieew session policy aan 
4. Maak deze policy zodat het aan de behoefte voldoet die nodig zijn. Je kan hier instellen dat het real time scanning moet doen.

---