## REST API

### Authenticatie

Elk request naar de API moet voorzien worden van de **API key** en **API secret** in de Basic Auth headers. Deze credentials bepalen tot welke boxen er toegang is.

*Let op*: de API credentials zijn enkel nodig bij het aanroepen van de REST API. Bij de [Viewer API](viewer-api.html) verloopt de authenticatie middels [JWT](https://jwt.io).

### HTTP Status codes

Als REST API wordt gebruik gemaakt van standaard HTTP status codes:

* 200 - OK: Success
* 404 - Not found: wanneer er bijvoorbeeld een bericht of box wordt bevraagd die niet bestaat.
* 400 - Bad request: wanneer het request ongeldig is.

De responses van de API zijn altijd in JSON format. De inhoud is afhankelijk van de status code.