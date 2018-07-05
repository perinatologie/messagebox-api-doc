---
id: content-types
---

## Content types

MessageBox kan berichten in verschillende formaten verzenden, ontvangen en tonen.

Elk bericht in MessageBox heeft een `content-type`. Deze wordt bijvoorbeeld meegestuurd bij het aanroepen van het [send endpoint](endpoint-send.html).

Afhankelijk van het `content-type` zal in de viewer API andere presentatie methoden worden gebruikt zodat er steeds nieuwe berichtformaten ondersteund kunnen worden.

### text/plain

In dit type bericht wordt in het `content` veld  platte tekst geplaatst, evt met line-breaks.

In de viewer wordt deze tekst as-is getoond.

Dit type bericht is voor simpele berichten tussen personen.

### text/markdown

In dit type bericht wordt in het `content` veld een markdown tekst geplaatst. Lees meer over [markdown](https://en.wikipedia.org/wiki/Markdown)

In de viewer wordt deze tekst als Markdown gerendered met headers, bold, italic, bullet lists, links e.d.

Dit type bericht is voor simpele berichten tussen personen met eenvoudige opmaak.


### text/html

In dit type bericht wordt in het `content` veld HTML geplaatst.

In de viewer wordt deze HTML as-is getoond.

Dit type bericht is voor geavanceerde opmaak in berichten tussen personen.

### text/xml

In dit type bericht wordt in het `content` veld ruwe XML geplaatst.

In de viewer wordt deze XML as-is getoond.

Dit type bericht is voor gestructureerde uitwisseling tussen applicaties waarvoor geen specifieke content-type is gedefinieerd.

### application/vnd.formidable.instance+json 

Dit type bericht bevat in het `content` veld een JSON string volgens de structuur van Formidable.

Dit type bericht is bruikbaar voor het ontvangen van beveiligde online web-formulieren.

### application/vnd.nl.perinatologie.resource+xml 

Dit type bericht bevat in het `content` veld een XML string volgens het Hub XML Formaat van perinatologie.nl [lees meer](https://doc.perinatologie.nl/formaat-doc/).

### application/vnd.edi.medvri+xml (MEDVRI)

Dit type bericht bevat in het `content` veld een XML string volgens het Zorgmail MEDVRY formaat.

In dit format kunnen bijvoorbeeld gedetaileerde contact gegevens van ontvanger, afzender en onderwerp (client) worden meegestuurd. Denk hierbij aan telefoon nummers, geboortedatum, BSN e.d.

De viewer zal deze meta-data automatisch presenteren in de HTML weergave.

In het MEDVRI formaat is ruimte voor een notitie in vrije tekst.


### application/vnd.edi.medlab+xml (MEDLAB)

Dit type bericht bevat in het `content` veld een XML string volgens het Zorgmail MEDLAB formaat.

In dit format kunnen bijvoorbeeld gedetaileerde contact gegevens van ontvanger, afzender en onderwerp (client) worden meegestuurd. Denk hierbij aan telefoon nummers, geboortedatum, BSN e.d.

In het MEDLAB formaat is ruimte voor gestructureerde uitslag gegevens. Denk hierbij aan onderzoek codes, boven/ondergrens van normaal waarden, en de ruwe uitslag ovv meeteenheden.

De viewer zal deze meta-data automatisch presenteren in de HTML weergave.


### application/vnd.edi.medspe+xml (MEDSPE)

Dit type bericht bevat in het `content` veld een XML string volgens het Zorgmail MEDSPE formaat.

In dit format kunnen bijvoorbeeld gedetaileerde contact gegevens van ontvanger, afzender en onderwerp (client) worden meegestuurd. Denk hierbij aan telefoon nummers, geboortedatum, BSN e.d.

In het MEDSPE formaat is ruimte voor gestructureerde gegevens over de specialist, en een notitie.

De viewer zal deze meta-data automatisch presenteren in de HTML weergave.



