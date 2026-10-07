---
tags: [operativo]
---
# Deploy e hosting

- Repository GitHub: `giampieroarminio-design/CONTEGGIO-ORE-AUDITORIUM`. File pubblicati: `index.html`, `aggiornamenti.txt`.
- Pubblicazione per **upload di file** sul web di GitHub ("Add files via upload"): nessun branch di sviluppo, nessuna CI.
- L'app è servita come pagina statica (probabile GitHub Pages: il banner iPhone rimanda a «l'indirizzo dell'app su GitHub»).
- Era stata sviluppata anche come **artefatto Claude**: il codice rileva `window.claude` (download/permessi) e adatta il backup; su iPhone dentro Claude i dati **non** persistono.
- Installabile come scorciatoia/PWA: il codice gestisce `display-mode: standalone` e `navigator.standalone`, ma **non** c'è manifest né service worker nel repo (non funziona offline: serve rete per font, pdf.js e casella).

## Aggiornare l'app
1. Modificare `index.html` incrementando `APP_VERSION`, `APP_DATE` e aggiungendo la riga in `APP_LOG`.
2. Caricare il file su GitHub.
3. Gli utenti ricaricano la pagina (nessun meccanismo di auto-update).

## `aggiornamenti.txt`
Prima riga = URL dello script Google (vedi [[Verifica aggiornamenti (casella)]]). Cancellare il file spegne la funzione.
