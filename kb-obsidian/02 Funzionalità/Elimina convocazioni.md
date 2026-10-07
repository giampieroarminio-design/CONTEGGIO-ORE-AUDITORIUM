---
tags: [funzionalità, dati]
---
# Elimina convocazioni (v23)

In [[Impostazioni]]. Cancella i turni **previsti** in un periodo Dal–Al; opzione *Includi anche i turni già confermati* (⚠️ cambia ore e saldo, avviso in rosso).
- Le assenze non vengono toccate.
- Conferma esplicita con conteggi.
- **Annulla l'ultima eliminazione**: l'elenco rimosso è salvato in `oreAuditorium.v1.eliminazione` e ripristinabile (reinserisce solo gli id mancanti).
- Lo stesso meccanismo di undo è usato da: sostituzione automatica di previsti obsoleti all'import e cambio cognome.
