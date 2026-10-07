---
tags: [storico, decisioni]
---
# Decisioni di progetto (dedotte dal codice)

> Il *perché* originale sta nelle chat di progetto, non accessibili: qui solo ciò che il codice rende evidente. Da integrare ([[99 - Lacune e domande aperte]]).

| # | Decisione | Evidenza |
|---|---|---|
| D1 | App a **file unico**, senza backend né build | `index.html` ospitato su GitHub |
| D2 | Dati **solo locali** (localStorage); privacy: il PDF non lascia il telefono | testi in Import; backup manuale |
| D3 | Solo il **confermato** conta nel saldo; il previsto è informativo | `conf()` ovunque |
| D4 | **Il PDF vale come legge** per i previsti non confermati | v42, `computeVanished` |
| D5 | I turni confermati/manuali non si sovrascrivono senza chiedere | `analyze`, `defAct` |
| D6 | Minuti interi, selettore a mezze ore | `buildT` |
| D7 | Contratto default **169 h** | `S.settings.contract` |
| D8 | Mesi senza dati **non** generano debito | `monthsWithData` |
| D9 | Giorno libero = promemoria; ferie/malattia/permessi contano di default, L.104 no finché confermata dal consulente | `aSel.count`, testi UI |
| D10 | Squadre/eventi temporanei (40 gg) e fuori dal backup per risparmiare quota | `pruneCrew`, `snapshot` |
| D11 | Cognome da **confermare** prima di importare (evita turni di un collega) | v40 |
| D12 | Aggiornamenti dei PDF via **Google Apps Script** + JSONP di scorta | v43 |
| D13 | Stato mai perso silenziosamente: toast di errore, undo eliminazioni, copia `.prima` | vari |
| D14 | Festivo prevale su domenica; patrono di Roma opzionale | `holidays`, `festive` |
| D15 | Accessibilità e mobile prima di tutto | CSS |
