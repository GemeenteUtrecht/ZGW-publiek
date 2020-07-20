## Autoriseren in de keten

Binnen het programma Klantgericht werken in ketens (KIK) werken we aan klant-tot-klant ketens die mogelijk meerdere processen, taakapplicaties en actoren van verschillende organisatieonderdelen bevatten. Dit betekent dat de autorisaties binnen de keten goed op elkaar afgestemd moeten zijn om een continue flow te waarborgen.
Medewerkers binnen de keten moeten bij de informatie kunnen die zij nodig hebben voor hun werk, terwijl informatie waar zij geen toegang tot hebben afgeschermd blijft. 

### Uitgangspunten autorisatiemodel:

- Taakapplicaties halen hun informatie uit de gezamenlijke datalaag
- Autorisatie op de datalaag wordt decentraal ingeregeld in elke taakapplicatie (laag 5 common ground)
- Indien autorisatie niet afdoende in de (legacy) applicatie kan worden ingeregeld, wordt hier een maatwerkcomponent voor naast de taakapplicatie gezet.
- We werken zoveel mogelijk vanuit rollen en groepen
- Taakapplicaties worden aangesloten op de IAM voorziening
- Bij het gebruik van documenten bij meerdere zaken, worden er kopieën van de documenten opgeslagen bij de betreffende zaken. (ipv te relateren naar dezelfde documenten)

### Waarop kunnen we dan autoriseren?

Niveau 1)  In OpenZaak kan een taakapplicatie in zijn geheel worden geautoriseerd op bepaalde zaaktypen icm vertrouwelijkheidsniveau en informatietypen icm vertrouwelijkheidsniveau. 

Niveau 2) In elke taakapplicatie kunnen specifieke gebruikers (rollen) worden geautoriseerd op bepaalde zaaktypen icm vertrouwelijkheidsniveau en informatietypen icm vertrouwelijkheidsniveau. Indien nodig kan er vanuit de taakapplicatie ook geautoriseerd worden op zichtbaarheid van een zaak, verantwoordelijk OO en losse zaken.

### Wat betekent dit voor de keten?
- Autorisaties in de taakapplicaties binnen een keten moeten door de beheerders goed op elkaar afgestemd worden. De ketenregisseur (?) houdt hier toezicht op.

### Praatplaat
![Praatplaat](https://github.com/GemeenteUtrecht/ZGW-Intern/blob/master/architectuur/09062020%20-%20Decentrale%20autorisaties.png)

### Te beantwoorden vragen
Dit document beschrijft hoe we ervoor zorgen dat, met het gekozen autorisatiestructuurscenario, over applicaties heen de gebruiker bij die gegevens kan waar hij bij mag en dat hij dan kan doen wat hij mag doen. Dus: een proces wordt ondersteund door meerdere applicaties. Elk van die applicaties is nodig om het proces uit te voeren. En elk van die applicaties kent een andere autorisatiestructuur. DE volgende vragen moeten beantwoord worden:
1. Een gebruiker moet toegang hebben tot elk van die applicaties om zijn deel van het proces uit te voeren. Hoe doen we dat?
2. Een gebruiker moet in elk van die applicaties alleen toegang hebben tot de zaaktypen waartoe die gebruiker vanuit zijn rol/functie gerechtigd is. Hoe doen we dat?
3. Een gebruiker moet in elk van die applicaties alleen toegang hebben tot de vertrouwelijkheidsniveaus waartoe die gebruiker vanuit zijn rol/functie gerechtigd is. Hoe doen we dat?
4. Een gebruiker moet in elk van die applicaties alleen die handelingen kunnen uitvoeren waartoe die gebruiker vanuit zijn rol/functie gerechtigd is. Hoe doen we dat?
5. Hoe zorgen we dat in de driehoek zaaktype, vertrouwelijkheidsniveau en functionaliteit de juiste combinatie van rechten wordt uitgedeeld aan een gebruiker?
6. Hoe gaan we om met de verscheidenheid aan autorisatiestructuren in applicaties? (Sommige applicaties zijn een open bak, sommigen hebben een zeer verfijnde structuur tot op veldniveau en alles wat ertussen zit) Welke technische en procedurele maatregelen kunnen we nemen? En welke (rest)risico's zijn er dan nog? 

