# Sophos samen met Microsoft Defender

#### Hoe werkt het dan
Microsoft Defender Antivirus (MDAV) heet 3 verschillende modi:
- Active mode
    MDAV is actief en beschermt het systeem tegen bedreigingen. Dit is de standaard modus.
- Passive mode
    MDAV draait op de achtergrond, voert geen actieve bescherming uit, maar blijft wel beschikbaar voor Endpoint Detection and Response (EDR) via Microsoft Defender for Endpoint.
- Disabled mode
    MDAV is volledig uitgeschakeld en kan niet worden gebruikt om het systeem te beschermen.

Als Sophos gebruikt wordt gebruikt als primaire antivurusoplossing, dan:
- Draait Microsoft Defender Antivirus in passive mode.
- Defender for Endpoint blijft actief en monitort het gedrag van het systeem.
- EDR (endpoint Detection and Response) zorgt ervoor dat verdachte activiteiten toch worden gedetecteerd, zelfs als Sophos ze mist.

---

###### Wat is EDR?
EDR (Endpoint Detection and Response) is een geavanceerde beveiligingslaag die verdachte of kwaadaardige activiteiten detecteert op basis van gedrag en context. Het is geen klassieke virusscanner, maar:
- Analyseert processen, netwerkactiviteit, scripts, en bestandsgedrag.
- Detecteert aanvallen die door de primaire antivirus glippen.
- Kan automatisch ingrijpen, zoals het isoleren van een apparaat, beeïndigen van processen, of automatisch onderzoek starten.

---

#### instellen 
1. Je moet defender in passive mode zetten. 
Dit gebeurd normaal automatisch als je het apparaat onboard.
Je kan dit controleren door dit uit te voeren in powershell:
```powershell
Get-MpComputerStatus
```

Als het niet in passive mode staat, kan je dit doen door het volgende commando uit te voeren:
```powershell
Set-MpPreference -PassiveMode $true
```

---
