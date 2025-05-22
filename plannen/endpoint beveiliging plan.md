## Endpoint
### Microsoft Defender for Endpoint
1. Ga naar https://security.microsoft.com/
2. Ga naar Settings > Endpoints > Onboarding
3. Volg de instructies om apparaten aan te sluiten op Microsoft Defender for Endpoint:
    - Kies het juiste besturingssysteem
    - Download het onboardingscript
    - voer het script uit op het apparaat
4. Controleer onder devices of het apparaat succesvol verbonden is

##### testen
om te testen of het apparaat goed is verbonden kun je dit volgende script uitvoeren op het apparaat in PowerShell:
```powershell
powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
```
Als je dan bij incidents en alerts ga kijken, komt er een nieuwe melding.

![test alert](image/endpointbeveiligingplan/test%20alert.png)

### ASR rules
1. Ga naar https://intune.microsoft.com/
2. Ga naar Endpoint security > Attack surface reduction
3. Maak een nieuwe policy aan
4. Kies de juiste platformen
5. Kies de juiste policy type
6. Kies wat je wilt doen met de policy en voeg de juiste groep toe waar je dit op wilt toepassen
7. Sla de policy op en activeer deze


### Device Control policies

1. ga naar https://purview.microsoft.com/
2. Ga naar Data Loss Prevention > Policy
3. Maak een nieuwe policy aan
4. Zorg ervoor dat alleen device is aangevinkt bij location 
5. Maak een nieuwe rule aan 
6. Bij condition kies je File type (of iets wat je wilt)
7. Bij action kies je "Audit or restrict activities on devices" en zet je copy to a removable USB device op Block
8. Slaag de policy op en activeer deze

Dit kun je ook doen in https://security.microsoft.com/

verschil is dat je via purview kunt instellen welke data er niet op de usb mag komen en dat je via security.microsoft.com alleen kan instellen dat het niet mag (dat het alles blokkeert) naar niet goedkgekeurde devices.

### Threat and Vulnerability Management
1. Ga naar https://security.microsoft.com/
2. Ga naar endpoints > Vulnerability management > Dashboard
3. Activeer Threat & Vulnerability Management indien nog niet geactiveerd
4. Bekijk hier:
    - Software inventory
    - Beveiligingsadviezen
    - Prioritering op basis van risico en impact



#### Secure Score
1. Ga naar https://security.microsoft.com/
2. Ga naar Exposure Management > Secure score
3. Bekijk hier de score en de aanbevelingen
