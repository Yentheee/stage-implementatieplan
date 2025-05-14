### cloud-discorvery
#### Defender for Endpoint
1. Ga naar https://security.microsoft.com/
2. Ga naar Cloud apps > Cloud Discovery
3. hier kun je dan alles zien van welke apps er gebruik gemaakt wordt en hoe vaak deze gebruikt worden op de apparaten die in Defender for Endpoint zitten.


#### Sophos 
1. Ga naar https://security.microsoft.com/
2. Ga naar Cloud apps > Cloud Discovery
3. Ga dan naar Actions en kies creat new Cloud Discovery report
4. Hier kun je dan de logs van de Sophos Firewall uploaden en zo kun je alle apps die gebruikt worden in kaart brengen.




### app-governance
1. Ga naar https://security.microsoft.com/appgovernance
2. Hier zie je een overzicht van de apps die toegang hebben tot de Microsoft 365-omgeving.
- Je kan hier de toegangrechten van de apps beheren.


### Conditional-access
1. Ga naar https://entra.microsoft.com
2. Ga naar Protection > Conditional access
3. Maak een nieuwe policy aan
- Je kan hier de policy zo inrichten dat het voldoet aan de eisen die je hebt. Dit kan bijvoorbeeld zijn dat je MFA moet gebruiken of dat je alleen toegang krijgt als je op een bepaalde locatie bent.




### data-loss-prevention
1. Ga naar https://purview.microsoft.com
2. Ga naar Data loss prevention > Policy
3. Hier kun je dan een policy aanmaken voor de verschillende locaties zoals Sharepoint, OneDrive en Exchange.
4. Maak een nieuwe rule aan. Gebruik bij Condition de optie Content contains sensitive info types en kies dan de gevoelige informatie die je wilt beschermen. (je kan sensitive info types ook zelf aanmaken)
5. Bij Action kies je de actie die je wilt uitvoeren als er gevoelige informatie gevonden wordt. Dit kan bijvoorbeeld zijn dat je een melding krijgt of dat de gebruiker een waarschuwing krijgt. Of blokkeer de actie.
6. Activeer de policy.

##### real-time-scanning
1. Ga naar https://security.microsoft.com
2. Ga naar Cloud apps > Policies > Policy management
3. Maak een nieew session policy aan 
4. Maak deze policy zodat het aan de behoefte voldoet die nodig zijn. Je kan hier instellen dat het real time scanning moet doen.