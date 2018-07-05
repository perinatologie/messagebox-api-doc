---
id: viewer-api
---

## Viewer API: vele berichtformaten - 1 viewer

MessageBox ondersteund een breed aanbod aan content types. Van EDI berichten tot XML, HL7, HTML, Markdown en nog veel meer. Ook komen hier continu nieuwe formaten bij. Om het eenvoudig te maken voor EPD leveranciers om deze grote wir-war aan formaten toch heel makkelijk te ondersteunen bied MessageBox een **Viewer API**.

Het idee is dat het EPD aleen de berichten lijsten ophaalt via [REST API](rest-api.html), en vervolgens de berichten toont via deze Viewer API.

### Viewer integratie opties

De Viewer kan op verschillende manieren gebruikt worden:

* Door een bericht in een nieuw venster te openen (goed voor desktop en mobile applicaties)
* Door het bericht in een iframe te openen (voor web-applicaties)
* Door het bericht (onafhankelijk van de bron) in HTML formaat te downloaden en te tonen binnen de web-, desktop-, of mobile applicatie.

Wij adviseren gebruik te maken van methode 2, de iframe methode. De reden hiervan is dat een EPD vaak erg privacy gevoelige informatie bevat. Wanneer een applicatie zelf HTML uit externe bron toont binnen de eigen applicatie, dan ontstaan er al snel beveiligingsrisico's zoals Script Injection. Door gebruik te maken van de iframe methode is dit risico er niet en blijven eventueel onveilige scripts binnen de iframe en krijgen geen toegang tot de applicatie zelf. Deze methode wordt ook veel gebruikt in bijvoorbeeld webmail applicaties zoals Gmail, Hotmail e.d.

### Hoe gebruik je de Viewer API?

Wanneer je via de API een bericht of berichtenlijst ophaalt, dan bevatten deze een `xuid` en een `jwt`. Deze gebruik je om de **Viewer URL** samen te stellen:

```php
$viewerUrl = $baseUrl . ‘/’ . $boxName . ‘/messages/’ . $xuid . ‘?jwt=’ . $jwt;
```

De `$baseUrl` van de viewer van perinatologie.nl is `https://post.perinatologie.nl`.

Door deze viewerUrl in een iframe of WebView te gebruiken wordt het bericht weergegeven. Bijvoorbeeld:

```html
<iframe src=”{$viewerUrl}” style=”width: 100%;”></iframe>
```

De JWT verloopt automatisch waardoor de URL slechts voor een beperkte periode geldig is.
Het is dus niet aan te raden de url of JWT op te slaan in de applicatie, maar deze altijd op te vragen via de REST API op 't moment dat deze aan de eindgebruiker getoond moet worden.


