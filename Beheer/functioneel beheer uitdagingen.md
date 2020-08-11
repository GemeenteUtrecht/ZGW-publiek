Op het moment bestaan er voor functioneel beheer de volgende uitdagingen bij het inrichten van een keten:

1. De BPTL-tasks zijn dermate processpecifiek dat ze moeilijk te hergebruiken zijn.
1. Er is geen overzicht waar welke BPTL-tasks gebruikt worden. 
1. BPMN modellen worden onoverzichtelijk
1.1 Dit is gewoon iets wat gebeurt op het moment dat gemodelleerd wordt. Toch zou het wel fijn zijn om een manier te hebben om de overzichtelijkheid van een BPMN-model te bewaren. 
1. Er is geen rem op maatwerk
1.1 Doordat we zoveel in eigen beheer kunnen bouwen, kunnen we ook voldoen aan heel veel wensen van de business. Wat we in het oog moeten houden, is dat de oplossingen beheerbaar worden en dat we waar mogelijk gebruik maken van (aanpassingen op) bestaande oplossingen.  
1. Troubleshooten is lastig. Dit valt uiteen in drie delen:
  - Er is op veel plekken logging aanwezig die mogelijk duidelijk maakt waarom iets niet werkt. Dit is moeilijk in samenhang te zien.
  - Bij het bouwen van formulieren, is het lastig om de precieze naam van variabelen te weten en hoe je deze moet gebruiken
1. Het is ondoorzichtig wat de effecten zijn van een wijziging op één plek. Stel dat een variabele in een proces binnen Camunda anders wordt genoemd, kan dit een probleem in formulieren geven. Helaas is het onduidelijk in welke formulieren deze variabele wordt gebruikt. Dit kan onvoorzienen effecten hebben.
