:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 12 - 🇸🇪 Chifferteksten
 
I denne luken blir man spurt om å knekke koden til et chiffertekst som Alvepatruljen har klart å gjenskape:

![bilde](https://user-images.githubusercontent.com/15195014/210170410-1b5d2f5d-c343-421b-addb-fa643ad9c512.png)

Chifferteksten består av 4 deler. Den første virker til å være en linje med symboler. Andre del består av 4 linjer med en sirkel rundt første symbol på linjene. Tredje del er en sirkel med 26 symboler rundt seg. Siste del er også en linje, likt som den første, men her kommer også krøllparenteser frem noe som gir indikasjon på at dette kan være flagget.

Siden symbolene i chifferteksten ser ut til å representere tekst og at det er 26 bokstaver i det engelske alfabetet, kan vi prøve å konvertere symbolene til bokstaver med enkel substitusjon:

![bilde](https://user-images.githubusercontent.com/15195014/210170380-65cedd2d-b677-49ec-a452-a3a657359668.png)

Vi kan så prøve å oversette delene av chifferteksten, første del blir da:
![bilde](https://user-images.githubusercontent.com/15195014/210170483-c6928aea-43d7-40aa-b7b0-18dc310832a0.png)

Andre del blir:

![bilde](https://user-images.githubusercontent.com/15195014/210170525-99bacd3d-e464-428d-bbba-de342ed192b3.png)

Tredje del har allerede blitt oversatt med substitusjon. Siste del blir dermed:

![bilde](https://user-images.githubusercontent.com/15195014/210170549-922e90ed-4e29-43df-b6a2-84712450fb92.png)

Prøver vi å levere flagget slik det er får vi en melding på at det er feil. Dette gir mening, da større deler av chifferteksten fortsatt fremstår som ukjent for oss. For å komme oss videre kan vi prøve å google navnene som dukket opp:

![bilde](https://user-images.githubusercontent.com/15195014/210170643-74b3990b-45f9-42e6-beee-0ef9dcddd1f3.png)

Første resultat fra søket ender opp med en Wikipedia side på Blaise de Vigenère, hvor det kan bli sett at navnene vi har fått oppgitt dukker opp. Det kan også bli sett at personen er kjent for å være en kryptograf som er kjent for Vigenère chifferet.

Siden flagget ikke ga et riktig svar, i første utgangspunkt kan vi nå anta at vi har med et Vigenère chiffer å gjøre. For å dekryptere et Vigenère chiffer trenger vi den krypterte teksten og en nøkkel. Vi har teksten, men enda ingen nøkkel. Hele poenget med dette er å gjøre en poly-alphabetic substitusjon, som illustrert med kode nedenfor:

```c
char* Vigenere::GetNewKey(int textLength, int keyLength, char* key) {
  
  static char newKey[sizeof(key)];

  for (int i = 0, j = 0; i < textLength; i++, j++) {
    if (j == keyLength) {
      j = 0;
    }
    else {
      newKey[i] = key[j];
    }
  }

  return newKey;
}

void Vigenere::Encrypt(char* t, char* k) {
  int textLength = strlen(t);
  int keyLength = strlen(k);

  for (int i = 0; i < textLength; i++) {
    t[i] = ((t[i] + GetNewKey(textLength, keyLength, k)[i]) % 26) + 'A';
  }
}
```

Hvor for eksempel en kryptering klarteksten *"DAY"* med en nøkkel *"SEE"* ville blitt kryptert til *"VEC"*. Den poly-alphabetic substitusjonen kan i dette tilfellet også bli visuelt fremstilt som:

![bilde](https://user-images.githubusercontent.com/15195014/210171167-6921038f-c63a-4ee6-9f87-4e2e9991f017.png)

Nå som vi har en forståelse for hvordan nøkkelen henger sammen med chifferteksten, kan vi prøve å finne en. Fra andre del av teksten, så var det som nevnt en sirkel rundt forbokstavene på navnene som dukket opp. Her finnes det flere mulige kombinasjoner, hvor den riktige ser ut til å være å legge sammen navne `[Blaise, Adrianus, Jean, Louis, Henry III]`, slik at vi får nøkkelen BAJLH.

Vi prøver dermed å se hva dette gir oss:

![bilde](https://user-images.githubusercontent.com/15195014/210171417-9f3d6987-f09a-4a09-9be3-0b489525ba8a.png)

Teksten vi får, nemlig "Copiale", er relatert til det kjente [Copiale chifferet](https://en.wikipedia.org/wiki/Copiale_cipher). Ser vi tilbake på chifferteksten i denne luken gir det også mening, symbolene fra teksten er noen av de samme som dukker opp i Copiale chifferet. Relasjonen til Sverige kan også bli sett i det faktiske Copiale chifferet, da det blant annet var to svenske forskere fra Uppsala universitet som var med å løse det kjente chifferet.

Nå som chifferteksten fra luke 12 er løst, kan vi levere flagget som BOUVET-JUL{COPIALE} for 50 poeng! 🎉

[Gå til neste luke](Luke13.md)&nbsp; :arrow_right:
