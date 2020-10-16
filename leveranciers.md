# Aansluiten op services van Gemeente Utrecht

Gemeente Utrecht heeft een aantal core-services draaien in de proeftuinomgeving die
gebruikt kunnen worden door leveranciers om hun eigen services/applicaties hierop
aan te sluiten.

Dit document beantwoordt vaak-gestelde vragen en kan gedeeld worden met leveranciers
die wensen aan te sluiten, testen en/of proof-of-concepts bouwen.

## Overzicht omgevingen

Er is op dit moment één omgeving - namelijk de proeftuinomgeving. Deze is
gekarakteriseerd door canonical URLs van services met de vorm
`subdomain.utrechtproeftuin.nl`.

Deze omgeving is een test/acceptatie-omgeving.

## Open Zaak

Open Zaak is beschikbaar op https://openzaak.utrechtproeftuin.nl

### API's

Open Zaak biedt de volgende API's aan:

* Catalogi API
* Zaken API
* Besluiten API
* Autorisaties API

Open Zaak _kan_ ook de Documenten API aanbieden, deze is echter uitgezet in Open Zaak.
Zie [Documenten API](#documenten-api).

### Documentatie

De landingspagina van Open Zaak verwijst naar de individuele API-documentatiepagina's,
waar je het volgende vindt:

- API documentatie (OpenAPI / ReDoc)
- API scopes die gebruikt worden voor applicatie-autorisatie
- Notificaties die verstuurd worden (zie [Open Notificaties](#open-notificaties))

Merk op dat in de footer ook algemene Open Zaak documentatie gelinkt wordt én de huidige
versie getoond worden.

### Credentials

Om met de API's van Open Zaak te kunnen communiceren heeft je applicatie credentials
nodig, namelijk: een `client ID` en een `secret`.

Met deze gegevens moet je een JWT genereren voor de calls naar Open Zaak. Merk op dat de
JWT's een geldigheidsduur van één uur hebben.

De JWT structuur is als volgt:

_Header_

```json
{
  "typ": "JWT",
  "alg": "HS256",
}
```

_Payload_

```json
{
  "iss": "<issuer (mag client ID zijn)>",
  "iat": 1593012133,
  "client_id": "<client ID>",
  "user_id": "<unique identificatie eindgebruiker>",
  "user_representation": "<vriendelijke weergave eindgebruiker>"
}
```

De signature moet gemaakt worden op basis van het `secret` volgens het HS256 algoritme.

**Credentials verkrijgen**

Functioneel beheer (Frank, Jurjen en Michelle) kunnen deze in principe uitgeven.

Bij de kick-off zal dit één van de eerste zaken zijn die we regelen.

Ter voorbereiding horen we graag welke [zaaktypen](#zaaktypen) er nodig zijn én welke
scopes je applicatie nodig heeft zodat we de autorisaties in kunnen stellen.

## Zaaktypen

Er zijn een aantal zaaktypen in Open Zaak ingericht om huidige processen te
ondersteunen. Het aanmaken van nieuwe zaaktypen is zeker ook mogelijk en waarschijnlijk
zelfs wenselijk om isolatie tussen projecten te borgen.

Afstemmen welke zaaktypen nodig zijn zal waarschijnlijk met Functioneel Beheer gebeuren.

## Documenten API

Momenteel staat de Documenten API gehost op https://drc.utrechtproeftuin.nl/. Dit is een
implementatie met Alfresco als achterliggende storage. De langingspagina verwijst ook
naar de API documentatie, gebruikte scopes en notificaties die verstuurd worden.

Deze implementatie heeft wat gekende issues - mocht je dus tegen onverwachte resultaten
aanlopen, maak dan even hier een Github issue aan, zodat je niet nodeloos op zoek gaat
naar fouten in de eigen implementatie die mogelijk door ons veroorzaakt worden.

Er komt een stabielere implementatie, maar het is afwachten op ontwikkelingen bovenop
Alfresco en/of ontwikkelingen in Open Zaak.

## Open Notificaties

Open Notificaties is de service verantwoorlijk voor het distribueren van notificaties.
Deze staat gehost op https://nrc.utrechtproeftuin.nl, waar je ook de API documentatie
en scopes documentatie kan vinden.

Open Zaak verstuurt notificaties als er mutaties uitgevoerd worden via de API's, en
andere applicaties kunnen zich via Open Notificaties hierop abonneren. Het is ook
mogelijk om jullie applicatie notificaties te laten produceren en deze via Open
Notificaties te distribueren.

Voor Open Notificaties is er ook een `client ID` en `secret` nodig, net zoals bij Open
Zaak.

## NLX

De meeste services worden via het demo netwerk van [NLX](https://nlx.io) ontsloten, je
kan deze terugvinden in de [directory](https://directory.demo.nlx.io/?q=utrecht)

Voor de Documenten API heb je de service `drc-cmis` nodig.

Aansluiten op het demo netwerk van NLX kan met self-signed certificaten, zie de
[documentatie](https://docs.nlx.io) hiervoor. Je dient hiervoor zelf een outway op te
zetten, en verbindt dan via de outway met de services.

Voor (pre)-productie heb je hiervoor een PKI Overheidscertificaat nodig.

## Overige applicaties

Op https://beheerconsole.utrechtproeftuin.nl vind je een overzicht van de behandelde
processen en applicaties die in de proeftuinomgeving draaien. Neem gerust een kijkje,
misschien staan er relevante apps tussen.

## Applicatie hosten op de Proeftuin-infrastructuur

De voorkeur van Utrecht gaat ernaar uit om applicaties te testen op de eigen
infrastructuur. Indien je dus wenst de applicatie te deployen in de proeftuin, dan kan
dat.

We ondersteunen echter alleen Docker images, in een publieke of private registry.

Je kan hiervoor het volgende aanleveren:

- Kubernetes YAML-bestanden
- een docker-compose bestand die de connectiviteit toont

Merk op dat we standaard een applicatie in multi-replica uitrollen. Sommige applicaties
hebben hiermee problemen (login-sessies, gedeelde file-system storage).

## Gebruik van testsets

Bij het testen van koppelingen gebruiken we gegevens uit de officiële testsets, hiermee voorkomen we het (per ongeluk) gebruiken van iemands echte gegevens.

[GBA-V testset](https://www.rvig.nl/documenten/richtlijnen/2018/09/20/testdataset-persoonslijsten-proefomgevingen-gba-v)

[KVK testset](https://www.kvk.nl/sites/aansluitendataservice/index.html#/testvoorziening)
