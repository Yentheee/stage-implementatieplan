# Authenticatie en Identiteit

### Maakt u gebruik van MFA voor alle gebruikers?
- **Waarom:** MFA vermindert het risico bij gestolen wachtwoorden
- **Actie:** Configureer Azure MFA via Condition Access Policies (zet eventueel SSO aan)
- [MFA](./plannen/authenticatie%20en%20identiteit.md###MFA)

### Hoe wordt er bepaald of een login verdacht is? Gebruiken jullie login- en gebruikersrisicodetectie?
- **Waarom:** Veel aanvaller zijn niet zichtbaar aan de oppervlakte, maar tonen zich via afwijkend gedrag
- **Actie:** Gebruik Microsoft Entra ID Protection om inlog- en gebruikersrisico's automatisch te detecteren
- [Entra ID Protection](./plannen/authenticatie%20en%20identiteit.md###Entra%20ID%20protection)

### Blokkeren jullie toegang op basis van locatie, apparaatstatus of gebruikersol?
- **Waarom:** Niet elk device of locatie is even veilig, rolgebaseerde toegangscontrole voorkomt dat een aanvaller toegang krijgt tot gevoelige data
- **Actie:** Zet Conditional Access policies op:
    - Locatiegebaseerd (bv. alleen vanuit Europa)
        - Configureer "Impossible travel" detection in Defender for Cloud Apps
    - Device Compliance via Intune
    - Role-based access control (RBAC) voor admins
- [Impossible travel detection](./plannen/authenticatie%20en%20identiteit.md###Impossible%20travel%20detection)

### Wie beheert jullie admin-accounts, en zijn die altijd actief of just-in-time?
- **Waarom:** Permanente adminrechten verhogen het risico op misbruik, ook bij interne dreigingen
- **Actie:** Implementeer PIM (privileged identity management) voor just-in-time toegang en logging
- [PIM](./plannen/authenticatie%20en%20identiteit.md###PIM)

