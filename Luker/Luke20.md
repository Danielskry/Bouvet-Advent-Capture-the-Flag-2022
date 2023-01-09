:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 20 - 👩‍💻 Alveutvikleren
 
I denne luken blir man spurt om man kan hjelpe en junior alveutvikler med å bygge videre på The JuleCentral. Alveutvikleren hadde fått en fil som alven skal bruke, men fortstod ikke helt hvordan man gikk frem. Filen var en `app.js` fil som inneholdt:

```Javascript
const express = require("express");
const jsonwebtoken = require("jsonwebtoken");

const JWT_SECRET =
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJDVkUtMjAyMi0yODUyMSI6IjA0MjYyMDIyIiwiQ1ZFLTIwMjItMTk3NiI6IjA4MzEyMDIyIiwiQ1ZFLTIwMTMtMjAwMDQiOiIwMjA2MjAyMiIsIkNWRS0yMDA3LTY3MzAiOiIwOTEwMjAwOSIsIkNWRS0yMDIxLTM0MjM1IjoiMDIxMTIwMjIiLCJDVkUtMjAyMC0xNjIwOSI6IkJPVVZFVC1KVUx7fSJ9.IvYXw7qUr7bPxrW4mB8NHQa1pOIMwZukQ7HCRVSwNsc";

const app = express();
app.use(express.json());

app.post("/login", (req, res) => {
  const { username, password } = req.body;
  console.log(`${username} is trying to login ..`);

  if (username === "evergreen2" && password === "evergreen2") {
    return res.json({
      token: jsonwebtoken.sign({ user: "evergreen2" }, JWT_SECRET),
    });
  }

  return res
    .status(401)
    .json({ message: "The username and password your provided are invalid" });
});
```

Rett ut fra filen virker det ikke til å være helt åpenbart hva man skal gjøre, men ser man nærmere på JWT Token'et finner man:

![bilde](https://user-images.githubusercontent.com/15195014/210173629-8eeb38f2-c8fa-49e8-866d-aea833205948.png)

Verdiene vi finner i Payload viser seg å være sårbarhetskoder og datoene på når de ble publisert i NIST:

![bilde](https://user-images.githubusercontent.com/15195014/210174147-3548b1c0-8c13-4d14-b2b7-f7fece5b4e8e.png)

Finner man dermed publiseringsdato for CVE-2020-16209, finner man også flagget. Etter et søk finner man at publiseringsdatoen for CVE-2020-16209 er 05/19/2022.

Med det så kan vi levere flagget som BOUVET-JUL{05192022} og få 20 poeng! 🎉

[Gå til neste luke](Luke21.md)&nbsp; :arrow_right:
