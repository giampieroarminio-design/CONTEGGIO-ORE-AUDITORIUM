---
tags: [panoramica, tecnico]
---
# Architettura e stack

## In sintesi
- **File unico** `index.html` (HTML + CSS + JS vanilla in una IIFE). Nessun build, nessun framework, nessun backend proprio.
- Font: **Figtree** (Google Fonts).
- **pdf.js 3.11.174** caricato *on demand* da cdnjs solo quando si importa un PDF (`loadPdfJs`). Senza rete l'import PDF non funziona → fallback "incolla il testo".
- Persistenza: **`localStorage`**, chiave `oreAuditorium.v1` (+ chiavi accessorie, vedi [[Conservazione e pulizia dati]]).
- Ospitata su GitHub (banner iPhone: «Usa l'indirizzo dell'app su GitHub»); in origine anche pubblicata come artefatto Claude (`window.claude.use('downloads')`): vedi [[Deploy e hosting]].
- Unico servizio esterno applicativo: **Google Apps Script** per la casella convocazioni ([[Verifica aggiornamenti (casella)]]), il cui URL è nel file `aggiornamenti.txt`.

## Struttura di `index.html`
| Righe (circa) | Contenuto |
|---|---|
| 1–285 | `<head>`, CSS (variabili tema, componenti) |
| 288–563 | Markup: pagina principale + fogli modali (`.ov`/`.sheet`) |
| 566–760 | Stato `S`, load/save, utilità tempo, **calendario festivo**, calcoli mensili |
| 760–1000 | Foglio turno, azioni rapide, settimana, festivi, riepilogo |
| 952–1315 | **Parser PDF** (`parseConvocazioni`, `pdfGeometry`) |
| 1317–1670 | Anteprima import, confronto (`analyze`), applicazione |
| 1672–1760 | Import da testo, impostazioni |
| 1760–1892 | Backup/ripristino |
| 1893–2027 | Scheda Variazioni |
| 2028–2172 | Scheda Assenze |
| 2174–2318 | Squadra |
| 2320–2500 | Verifica aggiornamenti |
| 2503–2600 | Evento, memoria, eliminazione periodo |
| 2602–2642 | Versione e `APP_LOG` |
| 2644–2809 | Ruota dei giorni |
| 2811–2918 | Avvisi memoria, banner, link diretti, avvio |

## Flusso
`load()` → `pruneCrew()` → normalizza nomi sala → `render()` + `showBanner()` + `agInit()` + `handleLink()`.
Ogni modifica: muta `S` → `save()` → `render()`.

## Stato globale `S`
`entries`, `abs`, `cov`, `agDone`, `pdfw`, `chg`, `settings` → dettaglio in [[Modello dati]].

## Pagine (tab)
**Turni** · **Variazioni** · **Assenze** (barra in basso con Inizio/Fine/+ solo su Turni).
