---
tags: [calcolo, assenze]
---
# Assenze conteggiate

Una assenza `{type, date, count, min}` entra nel calcolo solo se `count && min > 0` e `type ≠ libero`.

- Conta come ore lavorate: va in `cr` del mese, **riduce quel che manca alle 169 h** e alimenta il riporto.
- Visualizzata nel *trio* "Lavorate + Conteggiate = Totale" e nella barra (segmento viola).
- **Ferie, malattia, permessi**: conteggio attivo di default (8:00/giorno).
- **Legge 104**: spento di default finché il consulente del lavoro non conferma.
- Modificabile in ogni momento ([[Assenze]]).
- Il mese di un'assenza conteggiata è considerato "mese con dati" ([[Ore e banca ore]]).

⚠️ Il codice in origine (commento a riga 2028) dichiarava "solo la legge 104 può contare come ore"; la regola attuale è più ampia (v. [[Decisioni di progetto]]).
