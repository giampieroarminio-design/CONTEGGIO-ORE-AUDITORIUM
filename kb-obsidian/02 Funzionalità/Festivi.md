---
tags: [funzionalità, calcolo]
---
# Festivi

Link "Vedi i giorni festivi del mese" nel riepilogo. Mostra festività e domeniche del mese con ore lavorate in ciascuna ("non lavorato" se zero) e i totali *Festività*, *Domeniche*, *Insieme*.

## Calendario usato (`holidays(y)`)
Capodanno 1/1 · Epifania 6/1 · Pasqua (algoritmo gregoriano) · Lunedì dell'Angelo · Liberazione 25/4 · Festa dei lavoratori 1/5 · Festa della Repubblica 2/6 · **Santi Pietro e Paolo 29/6 (patrono di Roma, opzionale)** · Ferragosto 15/8 · Ognissanti 1/11 · Immacolata 8/12 · Natale 25/12 · Santo Stefano 26/12 · + **giorni aggiuntivi** in formato `gg/mm` separati da virgola ([[Impostazioni]]).

## Regole
- Conta solo il confermato.
- **Festività prevale su domenica** (se una festa cade di domenica è conteggiata come festività).
- Turni a cavallo di mezzanotte: ore divise tra i due giorni ([[Turni oltre mezzanotte]]).
- Le ore domenicali sono evidenziate in arancione.
