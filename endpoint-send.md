---
id: endpoint-send
---

## [POST] /{boxName}/send

Verzend een bericht. In de POST body wordt een enveloppe gestuurd in de volgende JSON structuur:

```json
{
  "id": "message1",
  "subject": "Hallo Jill",
  "from": [
    "displayName": "John Johnson",
    "address": "johnjohnson"
  ],
  "to": [
      [
        "displayName": "Jill Jackson",
        "address": "jilljackson"
      ]
  ],
  "dateTime": "2018-03-28 15:30:54",
  "contentType": "text/plain",
  "content": "Beste Jill,\nDit is een voorbeeld bericht.\nmvg John"
}
```

### Veld toelichting:

* `id`: Unieke identificatie voor het bericht bij afzender. Wordt niet verwerkt, maar is te gebruiken indien er vragen over een bepaald bericht zijn bij de afzender.
* `subject`: dit is de onderwerp regel die in de applicatie van de ontvanger getoond zal worden in de lijst. Betreft het bericht een bepaalde client of dossier, dan is het te adviseren deze in de subject te plaatsen.
* `from`: Een bericht heeft maximaal 1 afzender. De afzender heeft een `displayName` welke in de berichtenlijst getoond wordt, en een `address`. Lees meer over [adresen formaten](address-formats.html).
* `to`: Een bericht heeft minimaal 1, maar mogelijk meerdere ontvangers. Elke ontvangers heeft een `displayName` welke in de berichtenlijst getoond wordt, en een `address`. Lees meer over [addressen].
* `contentType`: Dit veld geeft middels een standaard mime-type aan welke inhoud er in het `content` veld is geplaatst. Lees meer over [content types](content-types.html).
* `content`: De daadwerkelijke bericht inhoud. Formaat is afhankelijk van het `contentType` van dit bericht.

### Verwerking

Een bericht dat wordt ingediend het `send` endpoint zal in de `OUTBOX` van de afzender (from address)
worden geplaatst.
Een achtergrond process verwerkt vervolgens periodiek alle berichten in de OUTBOX en verzend deze
op een methode die bepaald wordt op basis van het address formaat (zie ook [addressen](addressen)).
Na verzending wordt het betreffende bericht van de `OUTBOX` naar de `SENT` box verplaatst.

