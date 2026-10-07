---
tags: [funzionalità, ui]
---
# Ruota dei giorni

Selettore circolare (ruota) nella pagina [[Turni]], attivabile/disattivabile in [[Impostazioni]] ("Mostra la ruota dei giorni").

- 15 nodi giorno disposti su arco, passo **24°**, giorno selezionato ingrandito.
- Interazione: trascinamento (pointer events con inerzia), frecce tastiera, pulsanti ‹ Oggi ›, tocco su un giorno. Vibrazione 6 ms al cambio giorno (se supportata).
- Cambiando giorno cambia anche il **mese visualizzato**.
- Sotto la ruota la **scheda del giorno** con bordo colorato:

| Colore | Stato |
|---|---|
| Rosso | almeno un turno confermato |
| Blu | solo turni previsti |
| Arancione | assenza concordata |
| Verde | libero (giorno coperto da un PDF importato senza turni) |

- **Pallini** sotto ogni giorno: rosso (lavoro), blu (previsto), bianco (assenza), verde (libero in settimana già importata, v. 37–38). Domeniche e festivi: cerchio arancione.
- "Libero" verde solo se il giorno è nella copertura dei PDF importati (`S.cov` o settimana con dati importati): vedi [[Conservazione e pulizia dati]].

Storia: introdotta v29, rifinita v32, 37, 38.
