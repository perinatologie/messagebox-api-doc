---
id: index
---

# MessageBox API

## Inleiding

De PeriHub ondersteunt zowel Pull als Push verkeer.

Tbv Push verkeer wordt gebruik gemaakt van de dienst "MessageBox", onderdeel van perinatologie.nl, en onderdeel
van de PeriHub infrastructuur.

Gebruikers en applicaties kunnen gebruik maken van MessageBox mbv dezelfde gebruikersnaam/wachtwoorden en API keys
als voor alle andere diensten van Perinatologie.nl

Ook zijn de adressen van de berichten boxen gelijk aan de accountnamen binnen perinatologie.nl

MessageBox is vergelijkbaar met andere (zorg) berichtenboxen zoals Secure Email, Zorgmail, e.d. met een aantal voordelen:

* Uniforme gebruikersnaam/wachtwoorden en API keys tov andere Perinatologie.nl diensten
* Kostenloos voor alle deelnemende partijen
* Mogelijkheid voor versturen van bijlagen zoals PDFs (rodebandkaarten), DICOM beelden e.d.
* Communicatie niet alleen tussen zorgverleners, maar ook andere personen en instanties zoals de client zelf, statistiek beheerders, onderzoekers, e.d.
* Web-interface met ondersteuning voor de gangbare formaten die binnen het Perinatologie.nl netwerk worden uitgewisseld.


## Hoe werkt het?

Het concept is erg eenvoudig: Een verzendende applicatie stuurt een uitgaand request naar de MessageBox API ovv content en geadresseerde.

De geadresseerde stuurt een uitgaand request om nieuwe berichten headers op te vragen. Om de content op te halen wordt een tweede request verstuurd.

In deze opzet is al het verkeer uitgaand, wat voor firewalls en andere security maatregelen eenvoudiger te implementeren
kan zijn.

## Boxen en adressen

Binnen de PeriHub bestaan verschillende account-typen: user, organization en apikey.

De accountName is hierin altijd uniek, en wordt daarom ook gebruikt voor adressering.

Elk account kan mogelijk 1 of meerdere berichtenboxen hebben. De eerste box is altijd beschikbaar, en heeft de naam `default`.
Een gebruiker met naam `test` heeft dus een box die geadresseerd kan worden als `test/default`.
