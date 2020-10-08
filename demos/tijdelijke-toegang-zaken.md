# Tijdelijke autorisaties op zaken

Alle stappen zijn met je Utrecht-login uit te voeren. Waar nodig, switchen we via hijack
naar een andere gebruiker!

1.  Maak autorisatieprofiel voor behandelaars bezwaren:

    Dit zorgt ervoor dat we een profiel hebben wat toegang heeft tot de
    bezwaar-zaken. Vanaf deze zaken zou je dan de relaties met de vergunningzaak zien.
    Dit zit nog niet in het procesmodel, dus daar moeten we straks wat omheen werken.

    **Permissies om bezwaarzaken te behandelen**

    Deze permissie-set geeft rechten om bezwaarzaken te behandelen.

    - toevoegen permission set op https://zac.utrechtproeftuin.nl/accounts/permission-sets/add/
    - Naam: Bezwaren behandelen
    - Rechten:
        - `zaken:inzien`
        - `aakproces:usertasks-uitvoeren`
        - `zaakproces:send-bpmn-message`
        - `zaken:toegang-verlenen`
    - Catalogus: UTRE
    - Zaaktypen:
        - Bezwaar behandelen
    - Maximale vertrouwelijkheidaanduiding: Zeer geheim

    **Permissies om toegang te vragen**

    Deze permissie-set geeft rechten om toegang te vragen tot zaken waar je geen rechten
    op hebt.

    - toevoegen permission set op https://zac.utrechtproeftuin.nl/accounts/permission-sets/add/
    - Naam: Toegang vragen tot vergunningszaken
    - Rechten:
        - `zaken:toegang-aanvragen`
    - Catalogus: UTRE
    - Zaaktypen:
        - Aanvraag evenementenvergunning behandelen
    - Maximale vertrouwelijkheidaanduiding: Zeer geheim

    **Aanmaken van autorisatieprofiel**

    Dit laat straks de gebruiker toe om bezwaarzaken te behandelen en toegang te vragen
    tot evenementenvergunningzaken.

    - toevoegen autorisatieprofiel op https://zac.utrechtproeftuin.nl/accounts/auth-profiles/add/
    - naam: Jurist bezwaren
    - permission sets:
        - Bezwaren behandelen - Zeer geheim
        - Toegang vragen tot vergunningszaken - Zeer geheim

2.  Koppel autorisatieprofiel aan gebruiker

    Dit zorgt ervoor dat een gebruiker de rechten heeft om de bezwaarzaken in te kijken.

    - scroll naar beneden op https://zac.utrechtproeftuin.nl/accounts/auth-profiles/ om daar
      het aangemaakt autorisatieprofiel "Jurist bezwaren" te bewerken, en klik het aan
    - klink linksbeneden "Gebruiker toevoegen"
    - Selecteer de gebruiker "jurist" en bevestig

3.  Uitkiezen en voorbereiden van de zaken

    Hier zorgen we dat we een vergunningzaak bij de hand hebben waar je behandelaar bent.
    Behandelaars van de zaak mogen toegangsverzoeken beoordelen, die we straks dus maken.

    Ga vervolgens naar de lijst van zaken: https://zac.utrechtproeftuin.nl/core/zaken/

    - Klik de zaaktypen-filter aan bovenaan
    - Selecteer het zaaktype relevant voor de demo, om toegang te vragen.
        - Aanvraag evenementenvergunning behandelen
    - Kies zaak "ZAAK-2020-0000004461" - deze is voorbereid
    - Toon dat je behandelaar bent bij de zaak
    - Houd deze zaak open in een tab, zodat je de URL kan kopiëren straks

4.  Tijd om nu een andere gebruikersaccount te gebruiken!

    - Ga naar de admin > Accounts > Gebruikers
    - zoek de gebruiker "jurist" en hijack deze
    - het vervolg gebeurt met de gebruiker "jurist"

5.  Toon het effect van de permissies

    - Ga naar "Alle zaken"
    - Observeer dat je enkel zaken ziet van het zaaktype "Bezwaar behandelen"
    - Plak de zaak-URL uit stap 3 in de browser en stel vast dat je geen rechten hebt
    - Klik door op "request access" en voer het formulier op
    - je komt vanzelf op de zaak-lijst pagina uit
    - release nu de gebruiker "jurist" (hijack-balk, rechtsboven)

6.  Je werkt nu weer op je eigen persoonlijke account

    - Navigeer terug naar de homepage: https://zac.utrechtproeftuin.nl/
    - Op de "Access requests" tab zie je nu dat er een toegangsverzoek is
    - Klik de zaak "ZAAK-2020-0000004461" aan
    - Je kan het toegansverzoek beoordelen
    - Vink de checkbox aan naast de gebruikersnaam
    - Stel een vervaldatum in
    - Klik "approve"

7.  De jurist heeft nu een e-mail ontvangen (zou naar je Utrecht mail moeten gaan)

8.  Tijd om weer het perspectief van de jurist te bekijken:

    - Hijack de jurist
    - Navigeer naar de zaak-detail pagina: https://zac.utrechtproeftuin.nl/core/zaken/002220647/ZAAK-2020-0000004461/
    - Stel vast dat je nu wel permissie hebt om deze zaak in te kijken
