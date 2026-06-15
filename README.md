[README_preventivatore.md](https://github.com/user-attachments/files/28951185/README_preventivatore.md)
# 📋 Preventivatore AI — Termoflex Srl

Applicativo web con AI integrata per la generazione assistita di preventivi tecnici a partire da una richiesta cliente in linguaggio naturale.

**→ [Apri l'applicativo](#)** *(link disponibile dopo il deploy)*

---

## Il problema

Costruire un preventivo tecnico è un processo lento e soggetto a errori. Chi lavora nel service industriale lo sa: si riceve una richiesta dal cliente (spesso al telefono, spesso urgente), la si deve tradurre in voci di costo, stimare i tempi di intervento, applicare i listini, gestire le maggiorazioni per urgenza o fuori orario. Il tutto manualmente, spesso da memoria.

Il risultato è inconsistente: due operatori diversi producono preventivi diversi per lo stesso intervento. I tempi si allungano. Le voci vengono dimenticate. Il margine si erode.

---

## La soluzione

Un applicativo web che trasforma una descrizione in linguaggio naturale in una bozza di preventivo strutturata, pronta per la revisione umana prima dell'invio al cliente.

Il tecnico o il commerciale descrive la richiesta come la racconterebbe a voce — l'AI classifica l'intervento, seleziona le voci di costo appropriate dal listino aziendale, applica le maggiorazioni corrette e genera una bozza completa in pochi secondi.

---

## Come funziona

1. Si descrive la richiesta del cliente in linguaggio libero
2. Si seleziona tipo impianto e livello di urgenza
3. Si preme "Genera preventivo"
4. L'AI restituisce una bozza con voci, quantità, prezzi e note operative
5. Il tecnico rivede, aggiusta e invia al cliente

**Il principio è lo stesso dell'agente di triage:** l'AI accelera — l'umano decide.

---

## Cosa genera l'applicativo

| Sezione | Contenuto |
|---|---|
| Intestazione | Numero preventivo, data, cliente, badge urgenza |
| Tabella voci | Descrizione, dettaglio tecnico, quantità, U.M., prezzo unitario, totale riga |
| Totale | Imponibile + IVA 22% + totale complessivo |
| Note operative | Avvertenze tecniche, condizioni di accesso, raccomandazioni aggiuntive |

---

## Esempi di richieste gestite

- *"Compressore Atlas Copco GA11 fermo da stamattina, perdita olio dal separatore, 3 linee bloccate — intervento urgente oggi"*
- *"Gruppo frigo in allarme alta pressione, ventilatore condensatore fermo, probabile ricarica gas R-410A"*
- *"Manutenzione programmata annuale — 2 compressori + essiccatore, da fare sabato mattina"*
- *"Sostituzione pompa centrifuga 2" inox su circuito raffreddamento stampi"*

---

## Perché questo progetto

Ho costruito e gestito preventivi tecnici per anni nel service industriale. La parte più lenta non era sapere cosa fare — era tradurre la diagnosi in documento formale coerente, senza dimenticare voci, senza sbagliare i calcoli, senza perdere tempo a cercare le tariffe nel listino.

Questo strumento automatizza esattamente quella parte, lasciando al tecnico la responsabilità della revisione finale — che è dove il suo know-how fa davvero la differenza.

---

## Stack tecnico

| Strumento | Ruolo |
|---|---|
| HTML / CSS / JS | Applicativo single-file, zero dipendenze server |
| Claude API (`claude-sonnet-4-6`) | Generazione preventivo in JSON strutturato |
| Netlify Functions | Proxy serverless per la chiave API |

---

## Note tecniche

L'AI riceve nel prompt il listino completo di Termoflex Srl (tariffe manodopera, maggiorazioni urgenza/fuori orario, prezzi ricambi principali) e restituisce un JSON strutturato che viene renderizzato direttamente nell'interfaccia. Nessuna logica di calcolo lato client: tutto il ragionamento è delegato al modello.

La risposta viene validata e parsata prima del rendering — in caso di formato non valido viene mostrato un messaggio di errore.

---

## Autore

**Alessandro Dardi** — Operations & Digital Automation · Bologna
[Portfolio](https://alessandro-dardi.netlify.app) · [LinkedIn](https://www.linkedin.com/in/alessandro-dardi/)
