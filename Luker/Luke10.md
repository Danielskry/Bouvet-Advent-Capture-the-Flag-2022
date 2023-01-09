:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 10 - 🕹️ Spillportalen
 
I denne luken blir vi spørt om å gjøre en pentest på spillportalen til The JuleCentral. Oppgaven uttrykker bekymringer for portalen ikke har god nok sikkerhet.

Det første som møter oss når vi prøver å komme oss inn på spillportalen er et innloggingsfelt:

![bilde](https://user-images.githubusercontent.com/15195014/210172725-5249a875-7f5a-41d9-9409-6e2683e01f49.png)

Ved å lete litt rundt i koden på nettsiden finner man ut at passordet man kan bruke for å logge seg inn er oppbevart på client-side. Passordet finner man i filen `loginscript.js`:

```javascript
function check(a){"Javascript"==a.password.value?window.open("/game"):alert("Feil passord!")}
```

Ved å bruke passordet `Javascript` for å logge seg inn får man opp et Snake spill:

![bilde](https://user-images.githubusercontent.com/15195014/210172718-7dd65501-e1c0-4815-b01a-3d6f69e0a598.png)

Ved å fortsette trenden med å se på hvordan informasjon blir håndtert på client-side finner man funksjonen:

```javascript
function CheckScoreLimit(){
        if(localStorage.getItem('highscore') >= 1000000000) {
		fetch('/send')
            	.then(response => response.json())  
            	.then(json => {
                	alert(json.message);
            })
        } 
    }
```

Man ser da at feltet `highscore` i Local Storage på nettleseren kan brukes til sette en verdi `>= 1000000000` for å få en melding fra serveren på siden. 

Etter å ha satt en verdi som er lik eller større enn 1000000000 får man flagget BOUVET-JUL{CRO55_S1D3_SCR1PT1NG}. Vi kan dermed levere inn flagget for 40 poeng! 🎉

[Gå til neste luke](Luke11.md)&nbsp; :arrow_right:
