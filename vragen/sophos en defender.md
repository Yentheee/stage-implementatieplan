# Sophos samen met Microsoft Defender

### Samenwerking tussen Sophos en Microsoft Defender?
Hoewel Sophos en Microsoft Defender beide endpointbeveiliging bieden, kunnen ze in combinatie wordne ingezet om sterkere, meerlagige beveiliging te bieden. In deze opstelling fungeert Sophos als primaire beveiligingslaag, terwijl Microsoft Defender aanvullende functionaliteiten levert op het gebied van detectie, zichtbaarheid en integratie met andere Microsof-beveiligingstools.

---

##### Gelaagde beveiliging
Dood Sophos en Microsoft Defender naast elkaar te gebruiken, ontstaat een gelaagde beveiligingsmodel waarbij bedreigingen vanuit verschillende invalshoeken worden gedetecteerd en bestreden:
- **Sophos Intercept X (of Sophos MDR)** is verantwoordelijk voor real-time bescherming tegen malware, ransomware en andere geavanceerde bedreigingen.
- **Microsoft Defender** draait in passive mode en wordt gebruikt om aanvullende inzichten te leveren aan andere onderdelen binnen de Microsoft 365 E5 Security Stack zoals:
    - Microsoft Defender for Endpoint
    - Microsoft Defender for Cloud Apps
    - Microsoft Defender for Identity
    - Microsoft Defender for Office 365
    - Microsoft Defender for Cloud
    - Microsoft Sentinel
    - Microsoft Purview

---

##### Samenwerking in de praktijk
Ook in passive mode blijft Microsoft Defender bruikbaar voor:
    - **Threat Intelligence en signalisering** via Microsoft 365 Defender Security Center.
    - **Zichtbaarheid van endpoint-activiteiten** via Microsoft 365 Defender Security Center.
    - **Detectieregels en correlatie** via Microsoft Sentinel.
    - **Integratie met andere Microsoft-beveiligingstools** voor een holistische beveiligingsaanpak.

---

##### Voordelen van deze samenwerking
- Extra detectielaag: Als een dreiging door Sophos niet wordt opgemerkt, kan Defender deze mogelijk nog signaleren.
- Geavanceerde rapportage en onderzoek: Microsoft Defender for Endpoint kan nog steeds informatie verzamelen en doorgeven aan het Microsoft 365 Defender Security Center.
- Zero Trust ondersteuning: Door de integratie met Azure AD en Intune kan Defender aanvullen rol spelen bvinnen een Zero Trust-architectuur.
- Centrale monitoring: Door data van Sophos en Defender te combineren in Microsoft Sentinel, ontstaat er een centrale plek voor detectie, correlatie en incidentrespons.

---

##### Configuratie
[instellen + uitleg](../plannen/sophos%20en%20defender.md)

---