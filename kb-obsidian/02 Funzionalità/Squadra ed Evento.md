---
tags: [funzionalità, import]
---
# Squadra ed Evento

Dati letti dal PDF all'import (se *Salva la squadra* è attivo). Servono a vedere **con chi si lavora** e **che evento è**.

## Pulsante Squadra
Foglio con le persone dello **stesso evento** (cella Evento) nella stessa sala, per categoria, con gli orari del PDF:
Fonici · Palchisti · Tecnici luce · Macchinisti · Tecnici video · Facchini (solo numero) · categorie nuove (es. *Direttori di palco*, riquadro con bordo bianco).
- Riquadri **colorati come nel PDF** (colore letto dai riempimenti delle celle; palette di riserva `Q_DEF`).
- «tu» accanto al proprio cognome.
- Sezioni **"Nella stessa sala, prima di te / dopo di te"**: altri eventi della sala nello stesso giorno, ordinati per mediana degli inizi delle persone con nome (facchini esclusi, v39).
- Titolo breve + riepilogo `inizio – fine · N persone + M facchini`.
- Avviso: controllare sempre il PDF originale.

## Pulsante Evento
Mostra il testo della cella **Evento** del PDF, riga per riga come scritto.

## Conservazione
Squadre/eventi si tengono **40 giorni**, sono **esclusi dal backup** e si riottengono reimportando ([[Conservazione e pulizia dati]]). Struttura dati: `crew` = `[categoria, nome, inizio, fine]`, `others` = altri eventi ([[Modello dati]]).

Come vengono estratti: [[Parser PDF - dettagli tecnici]].
