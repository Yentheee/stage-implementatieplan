# Endpoint beveiliging

### Hoe worden nieuwe toestellen momenteel beveiligf bij uitrol?
- **Waarom:** Niet beveiligde endpoints vormen een directe ingang voor aanvallers
- **Actie:**
    - Sophos MDR/Intercept X als primaire bescherming
    - Microsoft Defender for Endpoint als secundaire bescherming
- [Microsoft Defender for Endpoint](./plannen/endpoint%20beveiliging%20plan.md###Microsoft%20Defender%20for%20Endpoint)


### Wat gebeurd er bij verdachte activiteit (bv. PowerSell-misbruik) op een toestel?
- **Waarom:** Veel aanvallen maken gebruik van legitieme tools zoals PowerShell
- **Actie:** Zet Attack Surface Reduction (ASR) rules aan in Defender for Endpoint (zoals blokkeren van Office-macro's, script misuse, etc.)
- [ASR rules](./plannen/endpoint%20beveiliging%20plan.md###ASR%20rules)

### Hoe beheren jullie USB, printers en randaapparatuur?
- **Waarom:** Ongecontroleerde apparaten zijn een veelgebruikte vector voor malware en datadiefstal
- **Actie:**
    - Device Control policies in Defender for Endpoint
    - Sophos Device Control 
- [Device Control policies](./plannen/endpoint%20beveiliging%20plan.md###Device%20Control%20policies)

### Hebben jullie zicht op bekende kwetsbaarheden in hardware/software?
- **Waaarom:** Kwetsbaarheden zijn de toegangspoort voor exploits
- **Actie:**
    - Activeer Threat and Vulnerability Management in Defender for Endpoint
    - Gebruik Secure Score om risico's en aanbevelingen op te volgen
- [Threat and Vulnerability Management](./plannen/endpoint%20beveiliging%20plan.md###Threat%20and%20Vulnerability%20Management)
- [Secure Score](./plannen/endpoint%20beveiliging%20plan.md###Secure%20Score)

