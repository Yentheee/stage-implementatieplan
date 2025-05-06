# Endpoint beveiliging

### Hoe worden nieuwe toestellen momenteel beveiligf bij uitrol?
- **Waarom:** Niet beveiligde endpoints vormen een directe ingang voor aanvallers
- **Actie:**
    - Sophos MDR/Intercept X als primaire bescherming
    - Microsoft Defender for Endpoint als secundaire bescherming


### Wat gebeurd er bij verdachte activiteit (bv. PowerSell-misbruik) op een toestel?
- **Waarom:** Veel aanvallen maken gebruik van legitieme tools zoals PowerShell
- **Actie:** Zet Attack Surface Reduction (ASR) rules aan in Defender for Endpoint (zoals blokkeren van Office-macro's, script misuse, etc.)

### Hoe beheren jullie USB, printers en randaapparatuur?