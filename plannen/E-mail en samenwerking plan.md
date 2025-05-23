
# Phishing aanvallen detecteren
## Defender

### Anti-Phishing Policies
1. Ga naar: [https://security.microsoft.com](microsoft security)  
2. Navigeer naar: Email & collaboration > Policies & rules > Threat policies
3. Klik op Anti-phishing > Create policy
4. Configureer:
   - Gebruikers of domeinen die beschermd moeten worden
   - Phishing threshold: stel de gevoeligheid in (Low / Medium / High / Aggressive)
   - Acties: verplaats naar quarantaine, voeg waarschuwing toe, log, enz.

#### Script
```powershell
Connect-ExchangeOnline -UserPrincipalName admin@domain.com

New-AntiPhishPolicy -Name "PhishingBescherming" `
  -PhishThresholdLevel 4 `
  -EnableMailboxIntelligence $true `
  -EnableUnauthenticatedSender $true `
  -EnableTargetedUserProtection $true

New-AntiPhishRule -Name "KoppelPhishingPolicy" -AntiPhishPolicy "PhishingBescherming" -RecipientDomainIs "domain.com"
```
Als je dit script uitvoert in PowerShell, wordt er automatisch een Anti-Phishing Policy aangemaakt. Je kunt hier de parameters aanpassen/toevoegen naar wens.

#### test
Je kunt in https://security.microsoft.com/antiphishing kijken of de policy goed is aangemaakt.

Ook kun je het nakijken door dit script uit te voeren:
```powershell 
# Vereist: Verbinding maken met Exchange Online
Connect-ExchangeOnline -UserPrincipalName admin@domain.com

# Stap 1: Toon de actieve AntiPhishPolicy
Write-Host "Actieve AntiPhishPolicy:" -ForegroundColor Cyan
Get-AntiPhishPolicy | Format-Table Name, Enabled, PhishThresholdLevel, EnableTargetedUserProtection, EnableMailboxIntelligence

# Stap 2: Toon gekoppelde regels
Write-Host "`nGekoppelde AntiPhishRules:" -ForegroundColor Cyan
Get-AntiPhishRule | Format-Table Name, AntiPhishPolicy, RecipientDomainIs

# Stap 3: Simuleer een verdachte e-mail (alleen observatie)
Write-Host "`nLet op: Je kunt phishing niet volledig simuleren met PowerShell alleen." -ForegroundColor Yellow
Write-Host "Stuur een testmail van een niet-vertrouwde afzender naar een gebruiker in je domein en controleer of deze wordt gemarkeerd, verplaatst of geblokkeerd." -ForegroundColor Gray

# Stap 4: Optioneel - Mail flow logs bekijken via Security & Compliance Center
Write-Host "`nOpen het Microsoft 365 Security & Compliance Center om de rapporten en meldingen te bekijken." -ForegroundColor Green
Write-Host "URL: https://security.microsoft.com/threatpolicy" -ForegroundColor Blue
```

---

### Spoof Intelligence (Tenant Allow/Block List)
1. Ga naar: [https://security.microsoft.com](microsoft security)
2. Navigeer naar Email & collaboration > Policies & rules > Threat policies
3. Klik op Tenant Allow/Block List
4. Voeg domeinen of afzenders toe die je wilt toestaan of blokkeren

Microsoft detecteert spoofing automatisch via:
- SPF / DKIM / DMARC controles
- Verdachte verzendservers
- Impersonatie van interne gebruikers of vertrouwde domeinen  
- AI geeft beoordeling of spoof legitiem is of niet

#### Script
```powershell
# Installeer en importeer de ExchangeOnlineManagement-module
Install-Module -Name ExchangeOnlineManagement -Force -Scope CurrentUser
Import-Module ExchangeOnlineManagement

# Verbind met Exchange Online
$adminUPN = "admin@domain.com"
Connect-ExchangeOnline -UserPrincipalName $adminUPN

# Voeg een spoofing-toegestane afzender toe
New-TenantAllowBlockListSpoofItems `
    -Identity Default `
    -Action Allow `
    -SendingInfrastructure "contoso.com" `
    -SpoofedUser "spoofed@example.com" `
    -SpoofType External

# Voeg een spoofing-geblokkeerde afzender toe
New-TenantAllowBlockListSpoofItems `
    -Identity Default `
    -Action Block `
    -SendingInfrastructure "maliciousdomain.com" `
    -SpoofedUser "spoofed@maliciousdomain.com" `
    -SpoofType External

# Toon bestaande spoofingregels
Get-TenantAllowBlockListSpoofItems | Format-Table SpoofedUser, SendingInfrastructure, SpoofType, Action

# Verbreek de verbinding met Exchange Online
Disconnect-ExchangeOnline -Confirm:$false

```
Als je dit script uitvoert in PowerShell, worden er automatisch spoofed sender toegevoegd. 1tje is allowed en de andere is geblockt. Je kunt hier de parameters aanpassen/toevoegen naar wens.

#### testen
Ga naar https://security.microsoft.com/tenantAllowBlockLis en kijk dan of de Spoofed senders zijn toegevoegd.

---

## Sophos Email Security

### Anti-Phishing Policies
1. Ga naar: [https://central.sophos.com](sophos central)
2. Navigeer naar: Email Security > Policies
3. Zet Anti-Phishing Protection aan:
   - Detecteert display name spoofing
   - Beschermt tegen imitatie van domeinen en gebruikers
   - Gebruik Advanced Settings voor aangepaste regels per gebruiker/domein

---

### Impersonation Protection
1. Ga naar: [https://central.sophos.com](sophos central)
2. Navigeer naar: Email Security > Policies
3. Zet Impersonation Protection aan
4. Voeg gevoelige interne personen
5. Sophos vergelijkt inkomende afzenders met deze profielen:
   - Detecteert lookalike domeinen
   - Detecteert naamsvervalsing

---

### URL Rewriting & Time-of-Click Protection
1. Ga naar: [https://central.sophos.com](https://central.sophos.com)
2. Navigeer naar: Email Security > Settings > Attachment and URL Protection
3. Zet URL Rewriting aan:
   - Links worden herschreven naar Sophos-scanning-URL’s
4. Zet Time-of-Click Protection aan:
   - Links worden realtime opnieuw gescand op moment van klikken
   - Beschermt tegen links die achteraf schadelijk worden

[sophos email protection](https://docs.sophos.com/central/customer/help/en-us/ManageYourProducts/EmailSecurity/EmailSecurityPolicy/index.html)

