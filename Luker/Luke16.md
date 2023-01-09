:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 16 - 👍 Sosiale medier
 
Her blir vi spurt om å sjekke sikkerheten til en sosiale medier webapp som har blitt laget for alvene, Nissefar og Nissemor. Går vi inn på appen dukker det opp noen SoMe innlegg fra alvene Evergreen2 og Snowball. 

![bilde](https://user-images.githubusercontent.com/15195014/210172280-067a8134-5a8f-4947-bb83-bf9b0ab55aa8.png)

Begynner vi å kikke litt rundt på kildekoden til siden ser vi blant annet en kommentar i HTMLen:
```html
 <!-- 
 Viktig at vi ikke indekserer siden vår (pga sikkerhet).
 Dette gjelder både konfigurasjonsfilene våre og her på
 static templates! 
-->
```

Fortsetter vi å lete litt rundt ser vi også hint om Cookies i det kommentarfeltet på Snowball sitt innlegg. Etter å ha sjekket hvilke cookies som kommer med på siden finner vi en merkelig cookie om `noindex`, som ikke gir noen mening å sette som en cookie:

![bilde](https://user-images.githubusercontent.com/15195014/210172328-4ac4b4b1-6d76-4c99-a103-db2ddd35796c.png)

Basert på HTML kommentaren og cookie'en virker det som om teksten i luke 16 stemmer. Webappen virker til å være preget av mye feil og mangler god sikkerhet. Inne i cookie'en vi finner så er det en link som tar oss videre til en passordbeskyttet Pastebin. 

For å finne passordet så leter vi rundt i Console på nettleseren:

![bilde](https://user-images.githubusercontent.com/15195014/210172596-764d2354-f2e6-4db1-8fbd-a93ce77d3d88.png)

Her får vi igjen bekreftet at det er noe muffens med cookie'en og i tillegg en rar tekst `APasswordiC1XgAfkhH`. Vi prøver å bruke dette som passord til Pastebin linken og får da fram flagget.

Nå som vi har funnet flagget BOUVET-JUL{GN0M3_C4V3} kan vi levere det inn for 30 poeng! 🎉

[Gå til neste luke](Luke17.md)&nbsp; :arrow_right:
