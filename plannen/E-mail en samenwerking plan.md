
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

