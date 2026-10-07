---
tags: [operativo, rischi]
---
# Problemi noti e rischi (revisione del codice, v46)

## Dati
1. **Single point of failure**: tutto in localStorage. Mitigazioni: backup manuale + promemoria. Nessuna sincronizzazione tra dispositivi.
2. Quota ~5 MB: squadre/eventi pesano; pulizia a 40 giorni.
3. Ripristino non ripristina `cov/agDone/pdfw/chg` (voluto).

## Sicurezza / privacy
4. L'URL Apps Script è **pubblico nel repo**: chiunque lo conosca potrebbe chiamare `list/get` se lo script non impone autenticazione. *Da verificare* lato script; valutare token o limitazione. Il file PDF contiene nomi di colleghi (dati personali di terzi).
5. `isEvalSupported:false` è già impostato per pdf.js. Output HTML con `esc()` quasi ovunque; i testi PDF (evento, crew) sono sempre passati da `esc`/`textContent`.
6. pdf.js e font da CDN esterni (nessun SRI).

## Codice
7. **Collisione CSS `.chk`**: definita due volte (riga 98 = riga checkbox flex; riga 253 = pastiglia arancione "Cambiato"). La seconda regola può alterare l'aspetto delle etichette checkbox (`label.chk`). *Da verificare a schermo.*
8. `eventAt` definita due volte (la seconda vince); commento "applica le scelte" duplicato: residui di refactor.
9. `surnameOk` si imposta a `true` ad ogni salvataggio con cognome non vuoto: la "conferma" si aggira salvando le impostazioni.
10. Parser vincolato al **layout** del PDF (costanti 303/347/830, regex `FACCHINAGGIO DI PARCO`): se l'ufficio cambia modello, l'import fallisce (fallback testo).
11. Nessun test automatico; logica di calcolo critica (banca ore, mezzanotte, festivi) senza copertura.
12. Nessun manifest/service worker: niente offline.

Vedi anche [[Idee e prossimi passi]].
