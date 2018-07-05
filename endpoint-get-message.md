---
id: endpoint-get-message
---

## [GET] /{boxName}/messages/{xuid}

Wanneer via de berichtenlijst een of meerdere berichten zijn gevonden kunnen de xuids worden gebruikt om de details van het bericht op te vragen. De response is identiek aan die van de berichten lijst, maar bevat via deze endpoint ook de bericht inhoud.

Wij adviseren om niet direct zelf ondersteuning voor de content te implementeren, in veel gevallen is het veel makkelijker om de berichten te tonen mbv de [Viewer API](viewer-api.html).
