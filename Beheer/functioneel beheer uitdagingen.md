Op het moment bestaan er voor functioneel beheer de volgende uitdagingen bij het inrichten van een keten:

1. De BPTL-tasks zijn dermate processpecifiek dat ze moeilijk te hergebruiken zijn.
---> Dit is eigen aan flexibiliteit ervan. We zijn scherp bij de oplevering van losse onderdelen dat ze zo herbruikbaar mogelijk zijn (zoals adviseren/accorderen).

1. Er is geen overzicht waar welke BPTL-tasks gebruikt worden. 
---> Als functioneel beheerder wil ik een overzicht kunnen maken van BPMN-modellen waarin een bepaalde BPTL-topic, servicetask, formulier of variabele gebruikt wordt. (in volgorde prio).

1. BPMN modellen worden onoverzichtelijk
    - Dit is gewoon iets wat gebeurt op het moment dat gemodelleerd wordt. Toch zou het wel fijn zijn om een manier te hebben om de overzichtelijkheid van een BPMN-model te bewaren. 
---> Hier gaan we nu niets mee doen.
    
1. Er is geen rem op maatwerk. Doordat we zoveel in eigen beheer kunnen bouwen, kunnen we ook voldoen aan heel veel wensen van de business. Wat we in het oog moeten houden, is dat de oplossingen beheerbaar en aanpasbaar blijven. Waar mogelijk moeten we gebruik maken van (aanpassingen op) bestaande oplossingen.  
--> Met PO bespreken zodra dit teveel gaat gebeuren. Voor nu zelf scherp op blijven.

1. Troubleshooten is lastig. Dit valt uiteen in twee delen:
    - Er is op veel plekken logging aanwezig die mogelijk duidelijk maakt waarom iets niet werkt. Dit is moeilijk in samenhang te zien.
    - Bij het bouwen van formulieren, is het lastig om de precieze naam van variabelen te weten en hoe je deze moet gebruiken
---> Als functioneel beheerder wil ik bij alle errorlogging kunnen van alle componenten
---> Als functioneel beheerder wil ik één plek hebben waar ik alle errorlogging kan inkijken

1. Het is ondoorzichtig wat de effecten zijn van een wijziging op één plek. Stel dat een variabele in een proces binnen Camunda anders wordt genoemd, kan dit een probleem in formulieren geven. Helaas is het onduidelijk in welke formulieren deze variabele wordt gebruikt. Dit kan onvoorzienen effecten hebben.
---> Als functioneel beheerder wil ik alle documentatie op één plek en op dezelfde manier.
---> Als functioneel beheerder wil ik van elk onderdeel waar variabelen doorheen gaan de verplichte input en mogelijke output weten.
---> Als functioneel beheerder wil ik in OpenForms gebruik maken van invulbare JSON-sjablonen.
---> ALs functioneel beheerder wil ik documentatie over het gebruik van OpenForms met voorbeelden (van Json templates en variabele mapping).
