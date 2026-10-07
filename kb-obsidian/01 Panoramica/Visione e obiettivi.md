---
tags: [panoramica]
---
# Visione e obiettivi

**Autore**: Giampiero Arminio, sviluppata con Claude (Anthropic) — crediti nell'app: «Ideata e sviluppata da Giampiero Arminio, con Claude (Anthropic)».

## Problema
Il lavoratore ha un **monte ore mensile da contratto (default 169 h)** e una **banca ore**. Gli orari previsti arrivano ogni settimana in un PDF di convocazione condiviso con tutta la squadra; gli orari reali spesso differiscono (prolungamenti, uscite anticipate). Serve sapere in ogni momento: ore lavorate, saldo del mese, saldo banca ore con riporto, ore in festivi/domeniche, giorni liberi.

## Obiettivi
1. Inserire i turni in pochi tocchi (anche da notifica: [[Azioni rapide e link]]).
2. **Importare dal PDF** solo i turni a proprio nome ([[Import convocazioni PDF]]), senza inviare il file a server.
3. Distinguere **previsto** da **confermato**: solo il confermato conta nel saldo ([[Ore e banca ore]]).
4. Mostrare cosa cambia quando esce un PDF aggiornato ([[Cambi di turno]]).
5. Sapere con chi si lavora ([[Squadra ed Evento]]).
6. Proteggere i dati (solo in localStorage): [[Backup e ripristino]].
7. Produrre un **riepilogo testuale** del mese da condividere ([[Riepilogo mensile]]).

## Principi UX rilevabili dal codice
- Mobile-first (max-width 560 px, bottoni ≥44 px, safe-area iOS), tema chiaro/scuro automatico.
- Accessibilità: aria-label, focus-visible, `prefers-reduced-motion`.
- Conferme esplicite per azioni distruttive ("Tocca ancora per eliminare") e **annullamento** dell'ultima eliminazione.
- Messaggi in italiano colloquiale; nessun gergo tecnico verso l'utente.
