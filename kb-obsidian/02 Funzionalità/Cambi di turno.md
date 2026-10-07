---
tags: [funzionalità, import]
---
# Cambi di turno (v46)

Quando un PDF aggiornato modifica i turni dell'utente l'app lo **dice esplicitamente**.

## Tipi (`computeChanges`)
| Codice | Etichetta | Significato |
|---|---|---|
| `mod` | Cambiato | orario modificato (`prima → dopo`); abbina tolti e aggiunti dello stesso giorno per inizio più vicino |
| `sala` | Sala cambiata | stesso orario, sala diversa |
| `del` | Tolto | turno non più nel PDF |
| `add` | Nuovo turno | solo se il giorno era già coperto da PDF importato (`covHas`) |

## Dove si vede
1. **Anteprima import**: riquadro arancione "Cosa cambia per te".
2. **Banner** in alto finché non si preme "Ho letto" (`S.chg`).
3. Foglio "Cosa è cambiato nei tuoi turni".
4. Sul turno: "Cambiato · prima 14:00 – 19:00" / "Nuovo turno" (`e.chg`).

Pulizia: `S.chg` e `e.chg` spariscono per date passate ([[Conservazione e pulizia dati]]). Voci duplicate evitate con chiave `[data, tipo, a, b]`.

Dal v46 la **sala del PDF si applica sempre** (prima solo se mancante). Vedi [[Confronto e conflitti]].
