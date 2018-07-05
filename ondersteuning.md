## Ondersteuning
### Tips voor implementatie

* Gebruik de REST API om berichtenlijsten te tonen, en gebruik de Viewer API om de berichten te tonen. Op deze manier hoef je zelf geen ondersteuning te maken voor alle formaten die er in de zorg worden uitgewisseld. De berichtenlijst is ook universeel (onafhankelijk van formaat, afzender of gekoppelde dienst) en daardoor erg eenvoudig te tonen binnen de applicatie.
* Sla berichten niet op in eigen systeem. Laat deze staan bij MessageBox en maak gebruik van de API en Viewer om ze te tonen. Dat scheelt uitdagingen tbv synchroniseren, updaten e.d.
* De Viewer bied ondersteuning voor iFrame Resizer (https://github.com/davidjbradshaw/iframe-resizer) Gebruik deze library in de aanroepende pagina om automatisch de iframe hoogte aan te passen naar de inhoud. Zo is het voor de eindgebruiker niet meer zichtbaar dat er gebruik van een iframe wordt gemaakt, en bereik je een naadloze integratie in het EPD.
* Look & Feel van de viewer is op verzoek ook aan te passen naar de branding van het EPD. De Viewer werkt met Bootstrap 3 basis CSS, en kan middels eigen theme overrides worden aangepast naar eigen stijl. Op deze manier zijn lettertypen, kleuren e.d. In de viewer aan te passen naar het EPD.
Sla de JWTs niet op, deze zijn slechts beperkt houdbaar en mogelijk gekoppeld aan de sessie, IP e.d. Van de gebruiker. Hierdoor zal de link niet in andere sessies te gebruiken zijn.

### Voorbeeld client implementatie
Op GitHub (https://github.com/linkorb/messagebox-client-php) is de broncode van een voorbeeld PHP implementatie in te zien. Mogelijk bied deze code hulp bij het implementeren van de client library in andere programmeertalen.

### Contact
Bij vragen tijdens het implementeren van de MessageBox API kun je altijd contact met ons opnemen voor support. Stuur een mailtje naar info@perinatologie.nl, en we kijken graag met je mee!
