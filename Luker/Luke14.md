:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 14 - 🤭 Spøken
 
 Denne luken publiserte en binær melding som skulle inneholde en skjult tekst:

```
01001000 01110110 01101001 01110011 00100000 01100100 01110101 00100000 01100110 
01101111 01110010 01110100 01100101 01101100 01101100 01100101 01110010 00100000 
01100101 01101110 00100000 01101101 01100001 01110100 01110100 01100101 01101101 
01100001 01100111 01101001 01101011 01100101 01110010 00100000 01100001 01110100 
00100000 01101011 01110110 01100001 01100100 01110010 01100001 01110100 00100000 
01010010 01001111 01010100 01100101 01101110 00100000 01110100 01101001 01101100 
00100000 00110001 00110011 00100000 01101000 01100101 01101100 01110100 00100000 
01100111 01110010 01110101 01101110 01101110 01101100 01100101 01100111 01100111 
01100101 01101110 01100100 01100101 00100000 01100101 01110010 00100000 00110110 
00110100 00101110 00100000 01001000 01110110 01100001 00100000 01110110 01101001 
01101100 00100000 01101000 01100001 01101110 00100000 01110100 01110010 01101111 
00100000 01100001 01110100 00100000 01101000 01101010 01100101 01110010 01101110 
01100101 01101110 00100000 01100100 01101001 01101110 00100000 01100010 01100101 
01110011 01110100 11000011 10100101 01110010 00100000 01100001 01110110 00111111 
00100000 01001000 01101001 01101110 01110100 00111010 00100000 01010100 00110000 
01001010 01001001 01010011 01010110 01001010 01001000 01001100 01010110 01100100 
01001001 01010111 01011000 01110100 01011000 01010011 01000110 01101011 01111010 
01010110 01000101 01010101 01110111 01010010 00110011 00110000 00111101
```

Konverterer vi verdiene over til tekst får vi:
```
Hvis du forteller en mattemagiker at kvadrat ROTen til 13 helt grunnleggende er 64. 
Hva vil han tro at hjernen din består av? Hint: T0JISVJHLVdIWXtXSFkzVEUwR30=
```

Denne teksten gir indikasjon på at det finnes flere lag i teksten. Matematikken som blir nevnt i teksten gir ikke noen mening, men kan virke til å skjule en konverteringsmetode (Base64) og krypteringsmetode (ROT13). Vi prøver å konvertere teksten `T0JISVJHLVdIWXtXSFkzVEUwR30=` fra Base64 og får `OBHIRG-WHY{WHY3TE0G}`.

Nå begynner det å ligne på et flagg, da det har fått flaggformatet med symbolene `-`, `{` og `}`. Selv for det så er det fortsatt ikke helt i mål, siden det mangler riktig tekst med at det skal være noe som BOUVET-JUL{...}. Vi kan derfor prøve å dekryptere teksten `OBHIRG-WHY{WHY3TE0G}` med ROT13 substitusjon.

Etter å ha gjort det får vi flagget BOUVET-JUL{JUL3GR0T} som vi kan levere inn flagget for 10 poeng! 🎉

[Gå til neste luke](Luke15.md)&nbsp; :arrow_right: