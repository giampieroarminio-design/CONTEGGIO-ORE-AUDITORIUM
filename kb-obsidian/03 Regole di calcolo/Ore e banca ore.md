---
tags: [calcolo, core]
---
# Ore e banca ore

Tutte le durate sono in **minuti interi**. Formattazione `h:mm` (`fmt`), con segno nei saldi (`fmtS`).

## Durata di un turno
`dur = fine − inizio` (se negativo, +1440: [[Turni oltre mezzanotte]]). Senza fine ⇒ nessuna durata ("in corso").

## Mese `k`
- `w` = **ore lavorate** = somma durate dei turni **confermati** del mese.
- `cr` = **ore conteggiate** da assenze con `count` ([[Assenze conteggiate]]).
- `c` = ore da contratto (default 169 h = 10.140 min).
- **Totale** = `w + cr`.
- **Saldo del mese** = `w + cr − c`.
- **Mancano / superate** = `c − w − cr`.
- **Saldo banca ore a fine mese** = `riporto + saldo del mese`.

## Riporto `carry(k)`
`opening` + Σ per ogni mese *con dati* `m < k` (e `m ≥ openFrom` se impostato) di `(w_m + cr_m − c)`.
- "Mese con dati" = ha almeno un turno confermato con durata o un'assenza conteggiata con minuti > 0. **Mesi senza dati non sottraggono il contratto.**
- Se `openFrom` è impostato e il mese visualizzato è precedente, il saldo mostra "–" ([[Residuo di partenza]]).

## Solo il confermato conta
I previsti compaiono come "Previsti da confermare: ore (n)" ma non entrano in alcun totale (saldo, festivi, riepilogo, variazioni).

## Variazioni
`delta = dur(effettivo) − dur(previsto)` per turno con `ps/pe`; totale mensile sui confermati ([[Variazioni]]).

## Festivi/domeniche
[[Festivi]] — ore in festività e domenica, conteggiate sui pezzi giornalieri.

Codice: `workedIn`, `absMonth`, `carry`, `renderMain` (≈ righe 681–726).
