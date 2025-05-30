### Microsoft 365 Defender

1. Ga naar https://security.microsoft.com
2. Log in met je beheerdersaccount.
3. controleer of de volgende onderdelen zijn ingeschakeled:
    - Microsoft Defender for Endpoint
    - Microsoft Defender for Office 365
    - Microsoft Defender for Identity
    - Microsoft Defender for Cloud Apps
4. Ga naar Settings > Endpoints > Onboarding en zorgt dat alle apparaten zijn gekoppeld
5. Controleer onder Incident & Alerts of de medlingen correct binnenkomen.
6. Richt meldingsregels in onder Settings > Rules > Alert policies.

---

### Microsoft Sentinel
1. Ga naar https://portal.azure.com
2. Zoek naar Microsoft Sentinel in het zoekveld
3. Klik op +Add om een Sentinel-resource toe te voegen
4. koppel Sentinel aan een bestaande of nieuwe Log Analytics Workspace
5. Ga naar Content hub en voeg databronnen toe (zoals Microsoft 365 Defender)
6. Koppel ook Sophos MDR via: 
    - Data connectors > Sophos Cloud Optics
    - Data connectors > Sophos Cloud Security
7. Controleer binnen de Log Analytics Workspace of de logs correct binnenkomen.
8. Stel dataretentie en toegangsrechten in onder Settings > Usage and estimated costs

---

### Advanced Hunting
1. Ga naar https://security.microsoft.com
2. Klik op Advanced Hunting
3. Open eeen bestaande query of klik op New query
4. Gebruik KQL