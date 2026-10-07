---
tags: [dati, tecnico]
---
# Modello dati

Chiave `localStorage`: **`oreAuditorium.v1`** → JSON di `S`.

## `S`
```
entries[]  abs[]  cov[]  agDone{}  pdfw{}  chg[]  settings{}
```

### Turno (`entries[]`)
| Campo | Note |
|---|---|
| `id` | `t<timestamp><rand>` |
| `date` | `AAAA-MM-GG` |
| `start`, `end` | `HH:MM` effettivi; `end` vuoto = in corso |
| `ps`, `pe` | previsto da PDF (assenti per turni manuali) |
| `confirmed` | `false` = previsto; assente/true = confermato |
| `place`, `note`, `sala` | luogo (`Auditorium`/`Altro`), nota, sala |
| `vnote` | motivo variazione |
| `crew` | `[cat, nome, inizio, fine][]` |
| `others` | `{t, p:'a'|'b', c:crew[]}[]` altri eventi stessa sala |
| `evento` | testo cella Evento |
| `pdfAt` | data creazione PDF di origine (ISO) |
| `chg` | marcatore cambio non letto |

Categorie crew: `F` fonici, `P` palchisti, `L` luce, `M` macchinisti, `V` video, `X` facchini (nome = numero), `Z###` categorie nuove (hash del titolo colonna).

### Assenza (`abs[]`)
`{id:'a…', date, type: libero|ferie|malattia|permesso|l104, note, count?, min?}`

### Altro
- `cov[]`: intervalli `[da, a]` coperti da PDF importati (per i "giorni liberi" verdi).
- `agDone{nomeFile: data}`: convocazioni già gestite.
- `pdfw{lunedì: pdfAt}`: ultimo PDF importato per settimana.
- `chg[]`: `{d,k,a,b,at}` cambi non letti ([[Cambi di turno]]).
- `settings`: vedi [[Impostazioni]] più `cats` (palette categorie), `lastBackup`, `remindAt`.

## Chiavi accessorie
`.prima` (copia pre-ripristino) · `.eliminazione` (undo) · `.prova` (test conservazione) · `.test` · `.aggAt` (ultimo controllo casella) · `.agg` (link da file) · `.aggM` (link manuale).
