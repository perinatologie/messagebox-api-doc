---
id: index
---

# MessageBox API

MessageBox: De universele beveiligde berichten service voor de Zorg

Technische Implementatie Handleiding voor software leveranciers

## Inleiding

MessageBox is een universele berichten service voor de zorg.

De dienst is aan te sluiten op gangbare diensten als E.novation Vanad Zorgmail (zorgmail.nl), KPN E-zorg berichten service (ezorg.nl), reguliere e-mail en meer.

Daarnaast biedt MessageBox de mogelijkheid om direct te communiceren tussen aangesloten gebruikers, zonder deze berichten eerst via een externe dienst te routeren.

MessageBox is op 3 manieren te benaderen:

* Via een **web-interface**, via https://post.perinatologie.nl
* Via de **REST API** (https://post.perinatologie.nl/api/v1)
* Via een de **Viewer API** (https://post.perinatologie.nl/viewer)

Wanneer het EPD van de zorgverlener nog geen integratie biedt met MessageBox, dan kan de gebruiker toch al direct aan de slag, simpelweg door in te loggen via de web interface.

MessageBox is ook eenvoudig direct in EPD software te integreren door de leverancier. Hierbij kan gebruik worden gemaakt van de [REST API](rest-api.html) (om een overzicht te krijgen van beschikbare berichten), en de [Viewer API](viewer-api.html) (om het bericht te tonen, onafhankelijk van het type bericht).

MessageBox ondersteund via de Viewer een breed aanbod aan verschillende (zorg-specifieke) bericht formaten. Zo kunnen bijvoorbeeld de MEDVRI, MEDLAB, MEDSPE e.d. berichten worden getoond (onafhankelijk van hoe deze verzonden worden), maar ook Perinatologie.nl XML resources, of Text, HTML, Markdown berichten, en meer.

## Onderdeel van het perinatologie.nl platform 

De PeriHub ondersteunt zowel Pull als Push verkeer.

Tbv Push verkeer wordt gebruik gemaakt van de dienst "MessageBox", onderdeel van perinatologie.nl, en onderdeel van de PeriHub infrastructuur.

Gebruikers en applicaties kunnen gebruik maken van MessageBox mbv dezelfde gebruikersnaam/wachtwoorden en API keys als voor alle andere diensten van Perinatologie.nl

Ook zijn de adressen van de berichten boxen gelijk aan de accountnamen binnen perinatologie.nl

MessageBox is vergelijkbaar met andere (zorg) berichtenboxen zoals Secure Email, Zorgmail, e.d. met een aantal voordelen:

* Uniforme gebruikersnaam/wachtwoorden en API keys met andere Perinatologie.nl diensten
* In basis kostenloos voor alle deelnemende partijen
* Mogelijkheid voor versturen van bijlagen zoals PDFs (rodebandkaarten), DICOM beelden e.d.
* Communicatie niet alleen tussen zorgverleners, maar ook andere personen en instanties zoals de client zelf, statistiek beheerders, onderzoekers, e.d.
* Web-interface met ondersteuning voor de gangbare formaten die binnen het Perinatologie.nl netwerk worden uitgewisseld.

## Beveiliging

Voor het gebruik van de web interface is een perinatologie.nl ID benodigd. Deze is aan te maken via [www.perinatologie.nl](https://www.perinatologie.nl), klik vervolgens op “Aanmelden” rechtsboven.

De API is te benaderen vanuit software applicaties mbv een API Key. De API key wordt aangemaakt op naam van een Organisatie, en geeft toegang tot een of meerdere berichtenboxen.

De Viewer is te benaderen mbv JWT. In de meeste gevallen hoeft de leverancier hier niets extras voor te doen, de JWTs worden namelijke uitgegeven door de API en kunnen 1-op-1 worden gebruikt bij het openen van de Viewer.

## Hoe werkt het?

Het concept is erg eenvoudig: Een verzendende applicatie stuurt via de REST API een uitgaand request naar de MessageBox API o.v.v. content-type en geadresseerde(n).

Een geadresseerde stuurt ook een uitgaand request aan de REST API om nieuwe berichten headers op te vragen. Om de daadwerkelijke bericht inhoud (content) op te halen zijn er twee opties:

1. Stuur een tweede [REST API](rest-api.html) request om de ruwe bericht inhoud op te vragen
2. Open het bericht middels de [Viewer API](viewer-api.html) om het bericht altijd zo goed mogelijk te presenteren aan de gebruiker.

In deze opzet is al het verkeer uitgaand, wat voor firewalls en andere security maatregelen eenvoudiger te implementeren is.

## Boxen, adressen en toegang

Binnen de PeriHub bestaan verschillende account-typen: user, organization en apikey.

De accountName is hierin altijd uniek, en wordt daarom ook gebruikt voor adressering.

Er kunnen per box meerdere accounts worden toegevoegd die toegang krijgen tot de betreffende box.
Toegang kan worden verleend obv user accounts (voor inloggen op de web-viewer bijvoorbeeld) of een of meerdere API keys (tbv integratie in software applicaties).

Het is dus ook mogelijk om voor 1 organisatie of persoon meerdere boxen aan te maken.

