---
tags: [funzionalità, impostazioni]
---
# Impostazioni (⚙)

| Voce | Campo `settings` | Note |
|---|---|---|
| Ore mensili da contratto | `contract` (minuti) | Default **169 h**; accetta `169`, `169:30`, `169,5` |
| 29 giugno festivo | `patrono` | Default attivo |
| Altri festivi | `extra` | `gg/mm`, separati da virgola/;  |
| Ruota dei giorni | `wheel` | Default attivo |
| Salva la squadra all'import | `crew` | Default attivo; vedi [[Squadra ed Evento]] |
| **Cognome nelle convocazioni** | `surname`, `surnameOk` | MAIUSCOLO; chiave per leggere i PDF |
| Residuo banca ore da cedolino | `opening` (minuti) | `-50` o `12:30` |
| Dal mese / Anno | `openFrom` (`AAAA-MM`) | [[Residuo di partenza]] |
| Promemoria backup settimanale | `backupRemind` | Default attivo |

Altre sezioni nel foglio:
- **Copia di sicurezza**: file, testo, ripristino ([[Backup e ripristino]]).
- **Prova di conservazione dei dati** (2 passi) per browser che cancellano i dati.
- **Memoria dell'app**: occupazione su ~5.000 KB e "Svuota i dettagli dei PDF" ([[Conservazione e pulizia dati]]).
- **Elimina convocazioni** per periodo ([[Elimina convocazioni]]).
- Versione e "Novità delle ultime versioni" ([[Cronologia versioni]]).
- Diagnostica ("Informazioni tecniche sul salvataggio").

## Cambio cognome
Se cambia con turni previsti già importati ⇒ propone di eliminarli (con possibilità di annullare). I confermati e quelli manuali non si toccano. Dal v40 serve la **conferma del cognome** prima di importare PDF.

Nota: salvando le impostazioni con un cognome non vuoto `surnameOk` diventa `true` automaticamente.
