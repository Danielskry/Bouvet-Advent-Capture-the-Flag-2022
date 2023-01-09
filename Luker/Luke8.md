:arrow_left: &nbsp;[Gå tilbake til oversikten](../README.md)

# Luke 8 - 🗃️ Mystisk fil
 
Luke 8 forteller om at en av radarene til The JuleCentral har fanget opp en mystisk fil med sensordata. De sier så at selve filen ser ut til å være vanskelig å åpne og når den først åpnes vises kun tilfeldige tall. For å finne flagget må vi ta en nærmere kikk på filen `data.h5` som vi kan laste ned. 

En enkel måte å løse denne på er å åpne filen i en teksteditor og søke etter flagget "BOUVET-JUL{" og finne flagget. En annen litt mer komplisert måte er å prøve seg frem med litt Python og Regex:

```python
import numpy as np
import pandas as pd
import re
import h5py

hf = h5py.File('data.h5', 'r')

print(hf.keys()) # Finner et datasett `dataset_78`

df = pd.read_hdf('data.h5', 'dataset_78')
print(df) # Dataframe av datasettet ser ut til å inneholde tall

flagg = re.search(r'BOUVET-JUL{\w*}', df.to_string()).group(0) # Regex for å finne tekst
print(flagg)
```

Vi finner så flagget BOUVET-JUL{D4T4_FL4GG} som kan leveres inn for 40 poeng! 🎉

[Gå til neste luke](Luke9.md)&nbsp; :arrow_right: