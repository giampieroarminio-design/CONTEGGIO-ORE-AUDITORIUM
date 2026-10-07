---
tags: [dati, tecnico]
---
# Conservazione e pulizia dati

`pruneCrew()` all'avvio e dopo ogni import:

| Dato | Tempo di vita |
|---|---|
| `crew`, `evento`, `others` | **40 giorni** (dalla data del turno) |
| `agDone`, `pdfw` | 60 giorni |
| `cov` (copertura PDF) | rimossa se fine intervallo < oggi−60 |
| `chg` / `e.chg` | rimossi per date passate |
| **Turni, ore, assenze, impostazioni** | **mai cancellati** |

- Quota: ~5.000 KB (limite tipico localStorage); contatore in [[Impostazioni]] con la quota occupata dai dettagli PDF.
- "Svuota i dettagli dei PDF": cancella crew/evento/others e `cov`.
- Scrittura fallita ⇒ toast "Salvataggio non riuscito: fai una copia di sicurezza".
- Banner rosso se il browser non permette di salvare, o iPhone con pagina aperta dentro Claude (Safari cancella i dati). Prova di conservazione in 2 passi.
