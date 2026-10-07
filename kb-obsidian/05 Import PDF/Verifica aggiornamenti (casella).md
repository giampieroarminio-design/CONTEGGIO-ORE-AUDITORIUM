---
tags: [import, automazione, backend]
---
# Verifica aggiornamenti (casella)

Dal v43: l'app interroga una **casella dedicata** (Google Apps Script) in cui arrivano i PDF delle convocazioni, senza doverli scaricare a mano.

## Configurazione
- Il file **`aggiornamenti.txt`** nel repo contiene, nella prima riga, l'URL `https://script.google.com/macros/s/…/exec`. L'app lo legge ad ogni avvio (`cache:no-store`); se 404 spegne la funzione.
- Override per prove su un dispositivo: `?agg=<url>`; `?agg=off` per togliere.
- (L'URL non è riportato in questa KB di proposito: vedi [[Problemi noti e rischi]].)

## Protocollo (`agCall`)
`GET <url>?action=list` → `{ok, items:[{id,name,date}]}`
`GET <url>?action=get&id=<id>` → `{ok, data:<PDF in base64>}`
`fetch` con fallback **JSONP** (`callback=`).

## Nomi file attesi (`agParse`)
`<versione>. <gg> <mese> - <gg> <mese> <anno>.pdf` e varianti (`28-4 set-ott 2026`, mesi abbreviati/estesi, spazi/underscore, trattini lunghi). Il numero iniziale = **versione**; si tiene per ogni settimana solo la più alta. Candidate: settimane non terminate da più di 3 giorni (nomi non parsabili: ultimi 14 giorni).

## Quando controlla
All'avvio, al massimo ogni **3 ore** (`aggAt`), oppure a mano con "Verifica aggiornamenti". Se ci sono novità: banner "C'è un aggiornamento delle convocazioni" (Verifica / Più tardi).

## Riconoscere le già importate (v45, `agDetect`)
Scarica il PDF candidato, legge `/CreationDate` **senza aprirlo** e lo confronta con l'ultimo `pdfAt` locale della settimana (o copertura `cov`): più recente ⇒ *da importare*, altrimenti segnata in `agDone`.

L'import vero e proprio passa sempre dall'anteprima e dalla **conferma** ([[Import convocazioni PDF]]).
