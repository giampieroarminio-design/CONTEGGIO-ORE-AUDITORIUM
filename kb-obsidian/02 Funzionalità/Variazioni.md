---
tags: [funzionalità, ore]
---
# Variazioni (prolunga / anticipo)

Tab **Variazioni**. Serve a registrare di quanto gli orari reali si discostano dal previsto, a passi di **±1 ora** (limite ±12 h per lato).

## Meccanica
- Base di confronto: `ps/pe` (previsto PDF) se presenti, altrimenti `start/end` attuali.
- Due controlli: **Fine** (prolunga / uscita anticipata) e **Inizio** (anticipo / inizio posticipato).
- Anteprima "Ore effettive" e differenza rispetto al previsto.
- **Motivo** facoltativo (`vnote`), es. "fine montaggio, cambio palco".
- Opzione "Segna anche il turno come confermato" (per i previsti).
- "Torna al previsto" azzera.
- Se il turno non aveva `ps/pe` ma ha fine, al salvataggio `ps/pe` vengono fissati agli orari attuali.
- Se la fine non è inserita il controllo Fine è disabilitato.

## Elenco mensile
Variazioni del mese con delta per turno; **totale sui soli turni confermati** (verde positivo / rosso negativo). Compare anche nel [[Riepilogo mensile]].

## Etichette
Prolunga +h · Uscita anticipata −h · Anticipo +h · Inizio posticipato −h (colori in [[Turni]]).

Formula: `delta = durata effettiva − durata prevista` ([[Ore e banca ore]]).
