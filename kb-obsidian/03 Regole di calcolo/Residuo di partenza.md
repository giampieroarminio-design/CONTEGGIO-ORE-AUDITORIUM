---
tags: [calcolo, banca-ore]
---
# Residuo di partenza (v28)

Problema: l'app conosce solo i mesi registrati; la banca ore reale ha uno storico precedente.

Soluzione: in [[Impostazioni]] si indica il **residuo da cedolino** (es. `-50` = in debito, `12:30`) e il **mese da cui parte il conteggio** (`openFrom`).
- Il residuo vale **all'inizio** di quel mese; i mesi precedenti non si sommano più.
- Nel mese di partenza l'etichetta diventa "Residuo di partenza" invece di "Riporto precedente".
- Mesi prima di `openFrom`: saldo banca ore "–" ("il conteggio parte da …").
- Con "—" resta il metodo vecchio: parte dal primo mese registrato e `opening` si somma comunque.

Formula in [[Ore e banca ore]].
