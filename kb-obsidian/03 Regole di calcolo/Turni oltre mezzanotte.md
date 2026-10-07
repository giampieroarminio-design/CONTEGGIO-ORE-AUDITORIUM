---
tags: [calcolo]
---
# Turni oltre mezzanotte

Se `fine < inizio` il turno finisce il giorno dopo (basta indicare l'orario, nessun campo data fine).

- La **durata** è `1440 − inizio + fine`.
- Il turno resta assegnato al **giorno di inizio** (e quindi al mese di inizio) per elenco e ore lavorate.
- Per **festivi/domeniche** il turno si divide in due "pezzi" (`pieces`): minuti fino a mezzanotte sul giorno di inizio, il resto sul giorno successivo, ciascuno valutato per festività/domenica.
- Uguale inizio e fine ⇒ durata 0 (`b>=a`), non 24 h.
- Nelle Variazioni le differenze usano aritmetica modulare su 24 h (`diffMin`).
