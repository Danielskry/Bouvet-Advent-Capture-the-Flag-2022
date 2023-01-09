:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 2 - 🖥️ The JuleCentral

Andre luke introduserte en av flere oppgaver fra The JuleCentral. I dette tilfellet fikk man tilgang til en Development Terminal som man skulle utforske for å gi tilgangen tilbake til en av Nissefar sine alver. Det første som møtte oss i terminalen på plattformen til The JuleCentral var muligheten til å bruke kommandoen `help`:

![bilde](https://user-images.githubusercontent.com/15195014/210172647-12650c70-2e3b-4fe1-8505-3e40b92de939.png)

Ved å bruke kommandoen får man beskjed om at det finnes et admin passord og et [salt](https://en.wikipedia.org/wiki/Salt_(cryptography)) som skal sendes til alven. Leter man rundt i systemet med kommandoene `ls` og `cat` finner man en rekke filer som er tilgjengelig:

![bilde](https://user-images.githubusercontent.com/15195014/210092320-07d59375-a67c-4ac7-95b3-150f34236f6e.png)

I `.env` filen finner man en hemmelighet `SECRET_KEY` som er et salt:

![bilde](https://user-images.githubusercontent.com/15195014/210172656-b6ff50e7-ac43-436b-8d0d-6a59974fa4db.png)

Videre finner man en hemmelig melding i `remember.txt` filen:

```
aHVzayBhYSBmamVybiB0YWJlbGxlbiAncmFpbmJvdy5jc3YnIGZyYSBtYXBwZXN0cnVrdHVyZW4sIGplZyBoYXIgc2tqdWx0IGRlbiBmcmEgdGVybWluYWxrb21tYW5kb2VuICdscycgbWVuIGRlbiBlciBmb3JzdGF0dCBtdWxpZyBhYSBmYWEgYWFwbmV0IGRlbiBtZWQgJ2NhdCcu
```

Ved enten å gjenkjenne eller bruke et verktøy som [CyberChef](https://gchq.github.io/CyberChef/) (med valget Magic) ser man at dette er en Base64 dekodet melding. Etter å ha dekodet Base64 meldingen får man en beskjed:

```
husk aa fjern tabellen 'rainbow.csv' fra mappestrukturen, jeg har skjult den fra terminalkommandoen 'ls' men den er forstatt mulig aa faa aapnet den med 'cat'.
```

Filen `sprintplanning.txt` gir indikasjon om at kommandoene `ls` og `cat` ikke er tillatelse baserte, men også mulig å bruke på filer som har blitt skjult i systemet. I dette tilfellet så får man opplyst om at det finnes en fil `rainbow.csv`:

|Username|Hash  |
|--|--|
|rudolph  | 403e11a28a557c02de43300b342e2f26 |
|admin| 5ebe2294ecd0e0f08eab7690d2a6ee69|
|evergreen2| ced46b7f28bdfcd4d1daadc93a5eec3c|
|snowball| 7d9ba24dd7c262f603d9601e345183a8|

Tabellen inneholder kolonnene Username og Hash. Siden vi er på utkikk etter passordet til admin kan vi bruke admin sitt hash. For å gå fra et hash (one-way function) tilbake til den originale teksten kan vi prøve Google eller bruke et rainbow table. Filen `sprintplanning.txt` røper at det er MD5 hash. Etter for eksempel et kort søk finner vi ut at `5ebe2294ecd0e0f08eab7690d2a6ee69` blir om til `secret`.

Det eneste som gjenstår nå er å bruke vårt salt `s0mRIdlKvI` til å gjøre om `secret` til et salted hash. I filen `sprintplanning.txt` dukker det opp en URL som lar oss gjøre det. Etter å ha gjort dette kan vi bruke kommandoen:

```
$ send secret b36855251379b8f92dd72979987428cd
```

Vi får da flagget BOUVET-JUL{S4LT_PA55W0RDZ!!!} og kan levere det inn for 20 poeng 🎉

[Gå til neste luke](Luke3.md)&nbsp; :arrow_right:
