---
tags: [import, logica]
---
# Confronto e conflitti (`analyze`)

Per ogni turno del PDF, rispetto agli `entries` dello stesso giorno:

| Stato | Condizione | Azione predefinita |
|---|---|---|
| `same` | stesso orario (previsto o effettivo) | niente; eventualmente aggiorna **sala / squadra / evento** |
| `new` | nessun turno nel giorno (o solo previsti obsoleti) | aggiungi |
| `conflict` | nel giorno c'è già un turno non coincidente e non sostituibile | scelta utente |

Un turno esistente è **sostituibile da solo** se è previsto, importato da PDF, e non da un PDF più recente (`pdfAt`). Si chiede invece se è **confermato**, **manuale** o da **PDF più recente**.

## Scelte in caso di conflitto
- *Lascia com'è* (`keep`)
- *Cambia orario* / *Aggiorna il previsto* (`upd`): aggiorna `ps/pe`; se il turno segue il piano (o è previsto) allinea anche `start/end`; un confermato modificato a mano **conserva** gli orari reali.
- *Aggiungi come altro turno* (`add`)
Default (`defAct`): manuale ⇒ add; previsto ⇒ keep; confermato che segue il piano ⇒ upd, altrimenti keep. Se più turni PDF puntano allo stesso confermato, solo il più vicino lo aggiorna.

## Sostituiti dal nuovo PDF (`computeVanished`)
Turni importati nei giorni coperti che il PDF non contiene più (motivo: *sbarrato* o *non più presente*). Previsti ⇒ rimossi; confermati ⇒ **tenuti**; da PDF più recente ⇒ tenuti.

## Assenze
Turno in giorno con assenza ⇒ avviso; al conferma: "Sì, importa tutto" / "Importa saltando questi giorni" / "Torna all'anteprima".

Storia: v41 (ripristino scelta nei conflitti), v42 (sostituzione automatica), v46 (sala sempre applicata). → [[Cronologia versioni]]
