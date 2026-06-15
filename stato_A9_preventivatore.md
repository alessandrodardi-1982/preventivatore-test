# Stato Progetto A9 — Offerte e Preventivi

**Data ultima modifica:** 15 giugno 2026

---

## Descrizione
Applicativo web con AI integrata per la generazione assistita di preventivi tecnici. L'utente descrive la richiesta del cliente in linguaggio naturale, l'AI restituisce una bozza strutturata con voci, prezzi, IVA e note operative. Scenario fittizio: Termoflex Srl, Bologna.

**Numerazione portfolio:** A9 (dopo A8 — Gestione ricambi & magazzino)

---

## File prodotti

| File | Stato | Note |
|---|---|---|
| `preventivatore_ai.html` | ✅ Pronto | Applicativo completo con form + output AI |
| `README_preventivatore.md` | ✅ Pronto | Da rinominare in `README.md` al momento del caricamento |
| `claude-proxy.js` | ✅ Disponibile | Copiare dalla repo `alessandrodardi-1982/portfolio` |
| `netlify.toml` | ✅ Disponibile | Copiare dalla repo `alessandrodardi-1982/portfolio` |

---

## Cosa è completato

- [x] Interfaccia a due colonne: form richiesta (sinistra) + preventivo generato (destra)
- [x] 4 esempi rapidi cliccabili (compressore, frigo, manutenzione programmata, pompa)
- [x] Selettori tipo impianto e urgenza (standard / media / alta)
- [x] Campo cliente opzionale
- [x] Listino Termoflex completo nel prompt (manodopera, maggiorazioni, ricambi)
- [x] Risposta AI in JSON strutturato con parsing e rendering automatico
- [x] Output: tabella voci + totale IVA + note operative + numero preventivo progressivo
- [x] Badge urgenza colorato (verde / amber / rosso)
- [x] Bottone stampa / salva PDF
- [x] Banner dati dimostrativi
- [x] README professionale scritto per recruiter/HR
- [x] Design coerente col portfolio (navy, accent #2ca1fe, Sora + DM Sans)
- [x] Repo test creata: `https://github.com/alessandrodardi-1982/preventivatore-test`

---

## Cosa manca per andare live

- [ ] **Crediti Netlify disponibili** — si ripristinano l'8 luglio 2026 (55 crediti attuali, insufficienti)
- [ ] Collegare repo test a Netlify e impostare variabile `ANTHROPIC_API_KEY`
- [ ] Verificare applicativo e generazione preventivo su Netlify test
- [ ] Se test ok → creare repo `preventivatore-ai` (produzione) e collegarla a Netlify
- [ ] Aggiornare link nel README con l'URL reale assegnato da Netlify
- [ ] Aggiungere card A9 nell'`index.html` del portfolio principale
- [ ] Deploy su repo `portfolio` (produzione) con la nuova card

---

## Repo e URL (da compilare dopo il deploy)

| Elemento | URL |
|---|---|
| Repo test | `https://github.com/alessandrodardi-1982/preventivatore-test` |
| Repo produzione | `https://github.com/alessandrodardi-1982/preventivatore-ai` |
| Netlify test | da assegnare |
| Netlify produzione | da assegnare |
| URL applicativo live | da assegnare |

---

## Note tecniche

- Il prompt include l'intero listino Termoflex — tariffe manodopera, maggiorazioni urgenza/fuori orario, prezzi ricambi principali
- L'AI risponde in JSON puro (no markdown, no testo aggiuntivo) — il prompt lo specifica esplicitamente
- Il JSON viene parsato con `JSON.parse()` dopo pulizia dei backtick residui
- Modello usato: `claude-sonnet-4-6`, max_tokens: 1000
- In caso di risposta non valida viene mostrato l'error-box senza crash dell'applicativo
