---
id: get-messages
---

## [GET] /{boxName}/messages


Dit end-point wordt gebruikt om voor een betreffende box de on-gearchiveerde message headers op te vragen.

Een voorbeeld response:

```json
[
    {
        "id": "acKZVvr3sc6x9MT2k-9Q0Q",
        "subject": "Dit is een voorbeeld bericht",
        "content_type": "text/markdown",
        "created_at": "2017-03-01 08:36:13",
        "seen_at": null,
        "archived_at": null,
        "from_username": "johnjohnson",
        "metadata": "important: true\r\ncolor: red",
        "from_name": "default",
        "from_account": "johnjohnson"
    },
    {
        "id": "x9MT2j3SQ0QacKZVvr3sc1",
        "subject": "Dit is een tweede bericht",
        "content_type": "text/markdown",
        "created_at": "2017-03-01 09:12:54",
        "seen_at": null,
        "archived_at": null,
        "from_username": "johnjohnson",
        "metadata": "important: false",
        "from_name": "default",
        "from_account": "johnjohnson"
    }
]
```

Voor elk bericht worden de volgende velden teruggegeven:

* id: unieke id van dit bericht binnen het Perinatologie.nl netwerk
* subject: bericht onderwerp, net als bij email.
* content_type: soort content, bijvoorbeeld `text/markdown`, `application/pdf`, `text/plain`, `hub/dossier`, enz
* seen_at: datum/tijd wanneer bericht voor 't eerst gezien is (de content opgehaald).
* archived_at: datum/tijd wanneer bericht door gebruiker is gearchiveerd (na verwerking)
* from_username: gebruikersnaam van de verzender
* metadata: key/value pairs, zelf te bepalen, te gebruiken voor filtering, en applicatie specifieke doeleinden (koppelen dossier bijvoorbeeld)
* from_name: box naam van verzender, tbv reply
* from_accountname: account naam van verzender, tbv reply
