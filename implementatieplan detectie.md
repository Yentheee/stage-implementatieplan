# Detectie

### Hoe krijgen jullie inzicht in incidenten en aanvallen over alle systemen?
- **Waarom:** zonder gecentraliseerde detectie mis je verbanden tussen aanvallen en incidenten
- **Actie:** 
    - Gebruik Microsoft 365 Defender XDR Portal 
    - Voeg Microsoft Sentinel toe voor SIEM en SOAR
- [Microsoft 365 Defender](./plannen/detect.md#Microsoft-365-Defender)
- [Microsoft Sentinel](./plannen/detect.md#Microsoft-Sentinel)

### Wie onderzoekt incidenten en hoe snel reageren jullie daar op?
- **Waarom:** Snelheid is cruciaal om schade te beperken
- **Actie:** Laat Sophos MDR incidenten oplossen
- [Sophos MDR](./plannen/detect.md#Sophos-MDR)


### Worden logs uit meerdere bronnen gecentraliseerd opgeslagen?
- **Waarom:** Belangrijk voor compliance en onderzoek   
- **Actie:** Koppel Microsoft Defender en Sophos MDR aan Microsoft Sentinel voor centrale logging
- [Microsoft Sentinel](./plannen/detect.md#Microsoft-Sentinel)


### Wordt er actief aan threat hunting gedaan?
- **Waarom:** Proactief zoeken naar aanvallen voorkomt schade
- **Actie:** 
    - Gebruik Advanced Hunting (KQL) in Microsoft 365 Defender
    - Bouw eigen queries en playbooks voor detectie op maat
- [Advanced Hunting](./plannen/detect.md#Advanced-Hunting)

