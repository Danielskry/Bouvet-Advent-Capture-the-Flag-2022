:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 6 - ❄️ Snøfnugg
 
I denne luken får man kun et mystisk bilde:

![bilde](https://user-images.githubusercontent.com/15195014/210095037-5007360c-55df-4e3b-b9ed-acb1bbd7c3ef.png)

Det gjelder da å finne et flagg som er blitt skjult i bildet. Ved å sjekke metadata til bilde finner man en kommentar "Har du hoert om LSB substitusjon?". Det gir indikasjon om at vi kan bruke LSB substitusjon for å finne flagget. Et nettbasert verktøy som Aperi'Solve vil lett kunne løse en utfordring som dette og finne flagget, men vi prøver oss frem med litt Python:

```python
from PIL import Image
import numpy as np

lsb_image = Image.open("../bilde.png")
data = np.array(lsb_image)
data = data & 1
new_img = Image.fromarray(data * np.uint(255))
new_img.show()
```

Det vi får ut av `new_img` objektet er en QR-kode:

![bilde](https://user-images.githubusercontent.com/15195014/210095071-0e6cf2e9-27f5-4e15-8d39-3a2ec394c8c4.png)

QR-koden gir flagget BOUVET-JUL{LSB_P1X3L5} som kan leveres inn for 30 poeng! 🎉

[Gå til neste luke](Luke7.md)&nbsp; :arrow_right:
