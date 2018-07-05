---
id: endpoint-legacy-send
---

## [POST] /{boxName}/default/send

**Let op**: dit is een endpoint dat voor oude implementaties nog actief is, maar zsm zal verdwijnen.
In plaats van dit end-point kan het nieuwe [send endpoint](endpoint-send.html) worden gebruikt.

Verzend een bericht. In de POST body worden de volgende gegevens meegestuurd in JSON formaat:

```json
{
  "from_username": "johnjohnson",
  "to": "jilljackson/default",
  "subject": "Hallo Jill",
  "content": "SGFsbG8gSmlsbCwgZGl0IGlzIGVlbiB2b29yYmVlbGQgYmVyaWNodC4=",
  "content_type": "text/plain",
  "metadata": "dGVzdDogdHJ1ZQ=="
}
```

Let op: de content en metadata worden in base64 formaat geencodeerd tbv ondersteuning
van alle typen documenten.
