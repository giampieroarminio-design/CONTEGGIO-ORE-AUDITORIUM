---
tags: [import, flusso]
---
# Import convocazioni PDF

Pulsante **Importa convocazioni** (da [[Turni]]). Il PDF **resta sul telefono**: è letto in locale con pdf.js (solo la libreria viene scaricata da cdnjs).

## Flusso
1. **Cognome**: deve essere impostato e **confermato** ([[Impostazioni]]); altrimenti l'import si blocca con messaggio.
2. Scelta file (o scarico dalla casella: [[Verifica aggiornamenti (casella)]]).
3. Per ogni pagina: testo + geometria (linee, riempimenti) → [[Parser PDF - dettagli tecnici]].
4. Metadati: `CreationDate` del PDF → `pdfAt` (per capire quale PDF è più recente).
5. **Anteprima** con confronto vs archivio ([[Confronto e conflitti]]), riquadro "Cosa cambia per te" ([[Cambi di turno]]) e sezione "Sostituiti dal nuovo PDF".
6. Pulsante riassuntivo: «Importa: 2 nuovi, 1 vecchio rimosso, 3 aggiornati, sala aggiunta a …».
7. Applicazione: aggiunge turni **previsti**, aggiorna, toglie obsoleti (con undo), salva categorie/colori, registra cambi, aggiorna copertura `cov` e `pdfw`, apre la settimana del primo turno.

## Esiti/messaggi
- Nessun turno a proprio nome / cognome non trovato → controllare cognome.
- Struttura non riconosciuta / data non leggibile → usare **"Oppure incolla il testo"** o mandare il PDF a Claude in chat.
- "N turni risultano sbarrati" (annullati).
- Righe incomplete saltate.
- "Controlla la data" se la data dedotta è incerta (>60 giorni da oggi o etichetta giorno non coerente).
- Se il PDF è **più vecchio** di uno già importato: avviso; i turni da PDF più recenti non si toccano.

## Import da testo
Una riga per giorno: `28/09 14:00-19:00` oppure più fasce `02/10 8:00-12:00 14:00-18:00`; accetta `AAAA-MM-GG`, `gg/mm[/aa]`; anno dedotto (mese a >6 mesi di distanza ⇒ anno ±1).

## Regola d'oro
*"Il PDF vale come legge"*: i turni importati ancora **previsti** e non più presenti vengono rimossi da soli; si chiede conferma solo se il turno era confermato, manuale o arrivato da PDF più recente.
