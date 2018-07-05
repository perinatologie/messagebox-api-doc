---
id: address-formats
---

## Adres formaten

Wanneer een bericht in de `OUTBOX` wordt geplaatst via de het [send endpoint](endpoint-send.html),
dan wordt deze middels een achtergrond process verzonden via verschillende transport methoden.
De transport methode wordt bepaald naar aanleiding van het adres formaat.
Na de daadwerkelijke verzending zal het bericht altijd van de `OUTBOX` naar de `SENT` box van de afzender worden verplaatst. In geval van een mislukte verzending zal het bericht in de `ERROR` box van de afzender worden geplaatst.

### MessageBox naam (default)

Wanneer de in het `to` veld het `address` veld een lowercase string met alleen cijfers en letters wordt gezet, dan zal dit als een MessageBox naam herkend worden.

Het bericht wordt dan as-is in de `INBOX` van de ontvanger (`address`) worden geplaatst.

### email address

Wanneer het `address` veld een e-mail adres bevat, dan zal het bericht via reguliere e-mail worden verzonden.

### zorgmail address

Wanneer het `address` veld een e-mail adres bevat dat eindigd op een zorgmail domeinnaam (bv `@lms.lifeline.nl`), dan zal het bericht via het zorgmail account van de afzender worden verzonden.

### KPN Ezorg address

Wanneer het `address` veld een e-mail adres bevat dat eindigd op een E-zorg domeinnaam (bv `@ezorg.nl`), dan zal het bericht via het KPN E-zorg account van de afzender worden verzonden. (*let op*: KPN E-zorg functionaliteit voor verzending is nog in ontwikkeling. Ontvangen is al wel mogelijk.)

### Overigen.

Andere API koppeling specifieke adressen zijn ook beschikbaar voor bijvoorbeeld landelijke registraties, SMS e.d. 

Daarnaast zijn er specifieke box-namen beschikbaar voor maatwerk aflever methoden. Denk ook hierbij aan landelijke registraties, onderzoeken, e.d.

Neem voor details contact met ons op.



