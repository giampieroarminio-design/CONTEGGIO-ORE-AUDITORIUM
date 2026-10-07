---
tags: [dati, backup]
---
# Backup e ripristino

I dati stanno **solo nel browser**: cancellando i dati di navigazione o cambiando telefono si perdono.

## Backup
- File `ore-auditorium-backup-AAAA-MM-GG.json` (`{app:'ore-auditorium', versione, exportedAt, entries, abs, settings}`).
- **Esclusi**: crew, evento, others, cov, agDone, pdfw, chg (si riottengono reimportando i PDF).
- Percorsi di salvataggio (in ordine): API `downloads` di Claude → download normale (pagina esterna) → download con testo di scorta (pagina intera servita da Claude) → Web Share con file → **testo da copiare**.
- Alternativa: "Crea copia" testo.
- Promemoria **settimanale** (banner "Hai fatto un backup?" con Fai/Più tardi/Non mostrare più).

## Ripristino
1. Carica file o incolla testo → verifica `entries` → mostra conteggio e intervallo date.
2. Conferma "Sostituisci i dati attuali": salva prima lo stato corrente in `…v1.prima`, poi sostituisce `entries`, `abs` e unisce le `settings`.

Diagnostica visibile in ⚙ (versione, memoria, vista, permessi, condivisione file, browser). Vedi [[Conservazione e pulizia dati]] e [[Problemi noti e rischi]].
