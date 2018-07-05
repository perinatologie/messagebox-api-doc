---
id: get-messages
---

## [GET] /{boxName}/messages

Dit endpoint geeft een lijst van beschikbare berichten weer in het eerder beschreven JSON format.

### Status filter

Standaard worden hier de berichten uit de INBOX getoond. Er kunnen ook berichten uit andere boxen worden opgevraagd mbv de `status` query parameter. Bijvoorbeeld:

* ?status=ARCHIVED: verwerkte berichten
* ?status=OUTBOX: te verzenden berichten
* ?status=SENT: verzonden berichten
* ?status=ERROR: mislukte verzendingen

### Voorbeeld response

Een voorbeeld response met 2 berichten:

```json
[
    {
        "xuid": "Xugls5miRxcZCER8MzRaQ",
        "direction": "IN",
        "contentType": "application/vnd.messagebox.envelope+json",
        "status": "INBOX",
        "jwt": "aWF0IjoxNTIHEFVA4QEMbSH2TN0OTk2MD1MjE5OTY...teLgrTVpxyMTk5OTYzNE6Qe",
        "properties": [],
        "envelope": {
            "id": "9D5DC002520140103120411@3",
            "contentType": "application/vnd.edi.medlab+xml",
            "subject": "Jansen",
            "dateTime": "2018-01-01T11:24:22.000+01:00",
            "from": {
                "address": "amsterdam@demolab.nl",
                "displayName": "Amsterdam Demo Lab"
            },
            "to": [
                {
                    "address": "50009999@lms.lifeline.nl",
                    "displayName": "50009999"
                }
            ],
            "headers": {
            }
        }
    },
    {
        "xuid": "TTkedZQT2NVpGRwHyYKAx",
        "direction": "IN",
        "contentType": "application/vnd.messagebox.envelope+json",
        "status": "INBOX",
        "jwt": "6MTUyMTk5OTYziJK...NH0.WGv5Rf_llQ7XY",
        "properties": [],
        "envelope": {
            "id": "10009C2018241020DA5120347@4",
            "contentType": "application/vnd.edi.medlab+xml",
            "subject": "Pietersen",
            "dateTime": "2018-01-01T11:00:00.000+01:00",
            "from": {
                "address": "amstelveen@ziekenhuis.nl",
                "displayName": "Amstelveen Ziekenhuis"
            },
            "to": [
                {
                    "address": "5000888888@lms.lifeline.nl",
                    "displayName": "5000888888"
                }
            ],
            "headers": {
            }
        }
    }
]
```

### Veld beschrijving messages

Elke message heeft de volgende velden:
* `xuid`: een unieke identifier (zie www.xuid.org voor meer informatie)
* `direction`: IN of OUT (is dit een inkomend of uitgaand bericht).
* `status`: INBOX, ARCHIVED, OUTBOX of SENT
* `jwt`: de JWT welke te gebruiken is om dit bericht te tonen in de Viewer (meer details verderop).
* `properties`: MessageBox bied de mogelijkheid om gebruikers of software applicaties eigen properties (key + value) aan een bericht te koppelen. Dit kan dan gebruikt worden om bijvoorbeeld een eigen indeling van berichten te maken, of deze aan clienten te koppelen op basis van bsn of clientnummer, etc. De invulling kan volledig bepaald worden door de software leverancier.
* `contentType`: het soort content van dit bericht. In 99% van alle gevallen zal dit 
 `application/vnd.messagebox.envelope+json` zijn. Dit wil zeggen dat dit bericht een messagebox envelope bevat in JSON formaat. De inhoud van de envelope is te lezen in het volgende veld:
* `envelope`: een universeel formaat envelope voor de daadwerkelijke inhoud. Een deel van de complexiteit van het ondersteunen van meerdere berichtenboxen is dat elk formaat en elke dienst zijn eigen envelope heeft. MessageBox maakt dit generiek zodat er maar 1 formaat hoeft te worden ondersteund.


### Veld beschrijving envelope

De envelop bevat de volgende gegevens:
* `id`: Unieke identifier zoals bepaald door de dienst. Kan gebruikt worden om support cases na te vragen bij de dienst leverancier, maar er wordt afgeraden deze ID als key in eigen EPDs te gebruiken. Kies voor dat doeleind de message.xuid.
* `subject`: Onderwerp van het bericht om te tonen in een berichten overzicht.
* `dateTime`: Datum en tijd van het bericht in standaard ISO formaat.
* `from`: Afzender ovv `displayName` (weergave naam) en `address`. Het adres is een, afhankelijk van het type berichtenbox een email adres, perinatologie ID of ander adres zoals gehanteerd binnen de gekoppelde dienst.
* `to`: 1 of meerdere ontvangers, ook ovv `displayName` en `address`.
* `headers`: Hierin worden optioneel headers (key+value) ingevuld wanneer de gekoppelde dienst deze aanbiedt.
* `contentType`: het soort inhoud binnen deze envelope. 

### Property filters

Dit endpoint kan ook alleen messages teruggeven waarvan de properties overeenkomen met een bepaald filter.

Voeg bijvoorbeeld `?_color=red` toe aan de endpoint URL om alleen messages terug te krijgen
waarvan de property `color` op `red` staat.

Deze functie kan gebruikt worden om applicatie-specifieke koppelingen te leggen:

* Koppel een bericht aan een client, dossier of andere applicatie-entiteit
* Houd applicatie specifieke statussen bij

Hierdoor is het niet nodig om de messages te synchroniseren met een applicatie database.
De messages kunnen verrijkt worden met properties om de benodigde eigen functionaliteit te implementeren.
