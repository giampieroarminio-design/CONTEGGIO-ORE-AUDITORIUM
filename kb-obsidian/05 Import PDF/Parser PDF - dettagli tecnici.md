---
tags: [import, tecnico, parser]
---
# Parser PDF — dettagli tecnici

Funzioni: `pdfGeometry` (operatori grafici), `colInfo`, `parseConvocazioni`, e helper interni. Tutto euristico sul **layout** del PDF di convocazione (tabella: giorno | sala | persone per categoria | evento | note).

## 1. Geometria (`pdfGeometry`)
Scorre la lista operatori di pdf.js tracciando CTM, clip e colore di riempimento:
- `hy`: linee orizzontali nere sottili (separatori di riga/blocco sala).
- `vx`: linee verticali nere (bordi colonne).
- `hl`: linee orizzontali piene colorate (separatori cella Evento).
- `strikes`: linee sottilissime e corte, di qualsiasi colore → possibili **barrature**.
- `diags`: segmenti **obliqui** tracciati (barrature disegnate a mano).
- `cf`: rettangoli riempiti colorati non neri → **colori di categoria**.

## 2. Colonne (`colInfo`)
Dalle intestazioni `SALA` e `NOTE` e dalle linee verticali: bordi sala (default 303/347), inizio note (830), colonna Evento (dal bordo destro Sala alla linea successiva) e linee di cella Evento.

## 3. Etichette giorno e blocchi
- Etichette `LUN 28`, `MAR 29`… a sinistra (x < bordo sala).
- Separatori `FACCHINAGGIO DI PARCO` (o `NO FACCHINAGGIO…`) delimitano i blocchi-giorno; se il numero di separatori = numero etichette li si usa, altrimenti si associa il nome all'etichetta più vicina (con avviso data).
- **Mese** scritto in verticale a sinistra (es. `L U G L I O`, `SETTEMBRE-OTTOBRE`): ricostruito unendo le lettere, serve a risolvere la data. Se illeggibile: ricerca del giorno coincidente più vicino a oggi in ±400 giorni (`farWarn` se >60).
- Data blocco = data della prima etichetta + indice blocco.

## 4. Il mio turno
- Regex sul cognome con confini non-lettera, solo x < colonna Note.
- I **due orari a sinistra** del nome (entro 80 px, stessa y ±2,5) sono *in* e *out* → `ps`, `pe`.
- Se nome o entrambi gli orari sono **barrati** ⇒ turno annullato (`struck`).
- `sala` (`salaAt`): testo nella colonna Sala fra due linee orizzontali; normalizzazione `700/1200/2800/CDJ` ([[Glossario]]).
- `evento` (`eventAt`): testo della cella Evento, riga per riga.

## 5. Squadra
- Intestazioni di categoria lette dalla riga alta (anche nuove, es. *Direttori di palco*): cluster per x; codice noto (L,M,F,P,V,X) o `Z`+hash. Serve ≥4 colonne, altrimenti fallback sui titoli noti.
- Ogni nome è assegnato alla colonna più vicina (tolleranza adattiva 14–40 px); numeri solo per Facchini (`X`), nomi non numerici altrove.
- Esclusi nomi barrati. `crewAt` limita alla cella Evento; `othersAt` raccoglie gli altri eventi della stessa sala (max 4, 30 persone ciascuno, titolo ≤300 caratteri).
- Colore categoria = riempimento cella intestazione (`catMeta`) → `settings.cats`.

## Limiti noti
Dipende dal layout attuale del PDF: un cambio di impaginazione richiede aggiornare costanti/regole (vedi [[Problemi noti e rischi]]). Funzione `eventAt` definita due volte (la seconda sovrascrive la prima).
