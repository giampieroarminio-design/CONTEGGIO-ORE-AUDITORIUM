---
tags: [funzionalità, automazione]
---
# Azioni rapide e link

## Barra in basso (solo pagina Turni)
- **Inizio ora**: apre il foglio con l'ora corrente arrotondata alla mezz'ora. Se oggi esiste un turno *previsto*, lo precompila (fine vuota) così da confermarlo.
- **Fine ora**: chiude il turno **aperto** più recente (senza fine); se non esiste avvisa e chiede anche l'inizio.
- **+**: nuovo turno.

## Link diretti (per notifiche / MacroDroid)
`…/index.html?azione=inizio` · `?azione=fine` · oppure `#inizio` / `#fine`. Eseguiti all'avvio (`handleLink`). Pensati per automazioni Android: una notifica "sei entrato/uscito?" che apre l'app già sul foglio giusto.

## Altri parametri URL
`?agg=<url-script>` prova la [[Verifica aggiornamenti (casella)]] su un solo dispositivo; `?agg=off` la spegne.
