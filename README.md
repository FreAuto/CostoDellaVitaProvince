# 🏙️ Il costo della vita nelle province italiane

Progetto di **Francesco Autorino** – Data Analyst.

🛠️ Strumenti: **Python · Excel · Power BI**

📊 Dati: **107 province**, redditi 2016-2024, prezzi delle case 2016-2025, benzina 2026.

📌 Dati ufficiali: Ministero dell'Economia (redditi), Agenzia delle Entrate – OMI (case), MIMIT (benzina).

---

## 🧭 1. Il progetto in breve

❓ **La domanda**: in quale provincia lo stipendio "rende" di più?

Le 5 domande più piccole:

1️⃣ 💶 Dove si guadagna di più?

2️⃣ 🏠 Quanto costano le case?

3️⃣ ⚖️ Quanti anni di reddito servono per comprare una casa da 80 m²?

4️⃣ 📈 Come sono cambiati redditi e case dal 2016 al 2024? E l'inflazione?

5️⃣ ⛽ Quanto pesa un pieno di benzina sul reddito di un mese?

---

## 🎯 2. I risultati principali

💶 Reddito medio di una provincia "tipo": **24.470 €** lordi all'anno.

🗺️ Al **Nord** si guadagna circa **6.500 €** in più che al **Sud** e nelle **Isole**.

🥇 **Milano** è prima (**34.000 €**). **Ragusa** è ultima (**17.700 €**).

🏠 Una casa costa in media **1.185 €/m²**: da **3.600 €** a Milano a **520 €** a Caltanissetta.

⚖️ Per una casa da 80 m² servono **3,8 anni** di reddito: **1,8** a Biella, **9,2** a Bolzano.

🔗 Dove si guadagna di più, le case costano di più (correlazione **0,63**).

📈 2016-2024: redditi **+20,6%**, inflazione **+20,9%**: il potere d'acquisto è **fermo**.

🏠 Le case invece sono **scese del 3,6%**. Eccezione: **Milano +28%**.

⛽ Un pieno da 50 litri vale il **5%** di un mese di reddito: **3,6%** a Milano, **6,9%** a Ragusa.

🏆 Lo stipendio rende di più a **Biella, Alessandria, Mantova, Pordenone, Piacenza**.

🔴 Rende di meno a **Imperia, Sassari, Barletta-Andria-Trani, Rimini, Grosseto**.

---

## 🛠️ 3. Perché questi strumenti

🐍 **Python**: unire 3 fonti diverse, pulire gli errori, calcolare indicatori e correlazioni, fare i grafici.

📗 **Excel**: un file facile da usare, con un **confronto tra 2 province** e un **calcolatore** con le formule.

📊 **Power BI**: la dashboard con la mappa delle province e i pulsanti per zona (Nord, Centro, Sud, Isole).

---

## 🔄 4. Il percorso dei dati

```
MEF redditi (9 zip) ─┐
OMI case (xlsx)  ────┼─► 01_scarica.py ─► 02_pulizia.py ─► ✅ 5 tabelle pulite ─┬─► 🐍 Python
MIMIT benzina ───────┘   (1GrezziNonPuliti)                 (2Puliti)          ├─► 📗 Excel
                                                                               └─► 📊 Power BI
```

🧹 **Cosa ho fatto durante la pulizia**

| Passo | Cosa | Risultato |
|---|---|---|
| 1 | Letti i redditi dei comuni, 9 anni (2016-2024) | 71.257 righe |
| 2 | Tolte le righe senza provincia valida; somme per provincia | 962 righe (107 province × anni) |
| 3 | Reddito medio calcolato **senza** la fascia "zero o meno" (redditi negativi) | niente salti strani |
| 4 | Letti i prezzi OMI di tutte le zone | 11.318 righe |
| 5 | Tenuta la media di **tutta la provincia** | 1.024 province × anni |
| 6 | Tolti 3 valori sbagliati (es. Frosinone 2018: 100.535 €/m²) e riempiti 35 anni mancanti | serie pulite |
| 7 | Aggiunto il prezzo della benzina self (15/10/2026, dal progetto Carburanti) | 107 province |
| 8 | Sardegna: crescita dei redditi non calcolata (le province sono cambiate) | 5 province |
| 9 | Calcolati gli indicatori e l'indice del costo della vita | 106 province su 107 |

⚠️ "NA" è la sigla di **Napoli**: ho letto i file in modo che non diventasse un "valore mancante".

🧮 **Gli indicatori**

| Indicatore | Come si calcola |
|---|---|
| Casa da 80 m² | prezzo al m² × 80 |
| Anni di reddito per la casa | casa da 80 m² ÷ reddito medio |
| Pieno | 50 litri × prezzo benzina self |
| Pieno sul reddito | pieno ÷ (reddito ÷ 12) |
| **Indice del costo** (0-100) | 70% classifica degli anni per la casa + 30% classifica del pieno sul reddito |

📌 Indice basso = lo stipendio **rende di più**. Indice alto = **rende di meno**.

---

## 📁 5. I file in questo repository

| File | A cosa serve |
|---|---|
| `README.md` | Questo file |
| `DESCRIZIONE_GITHUB.md` | Nome, descrizione e topics del repository |
| `00_LEGGIMI.md` (in ogni cartella) | Una spiegazione corta di quella cartella |

### 📂 01Python

| File | A cosa serve |
|---|---|
| `01_analisi_costo_della_vita.ipynb` | 📓 L'analisi completa con 9 grafici (si legge anche su GitHub) |
| `02_CONCLUSIONI.md` | ✅ Le risposte alle 5 domande |

### 📂 02Excel

| File | A cosa serve |
|---|---|
| `01_Costo_Della_Vita_Analisi.xlsx` | 📗 10 fogli: riepilogo, **confronto tra 2 province**, **calcolatore**, classifiche per zona e anno |

### 📂 03PowerBi

| File | A cosa serve |
|---|---|
| `01_CostoDellaVitaDashboard.zip` | ⭐ **La dashboard**: estrai lo zip e apri `CostoDellaVita_Dashboard.pbip` con Power BI Desktop |
| `02_CostoDellaVita_Dashboard.pdf` | 📄 La dashboard in PDF |
| `03_misure_DAX.txt` | 🧮 Le 13 misure DAX |

📊 **Le 5 pagine della dashboard**

1. **Panoramica**: 6 numeri chiave, l'Italia disegnata con le province (verde, giallo, rosso), redditi e anni per la casa per zona
2. **I redditi**: tutte le province, il reddito anno per anno, i contribuenti per fascia
3. **Le case**: anni di reddito per la casa, il prezzo anno per anno, redditi e case a confronto
4. **La classifica**: tutte le 107 province con l'indice del costo della vita
5. **Conclusioni**

🎛️ In alto si sceglie la **zona** (Nord, Centro, Sud, Isole) e tutti i grafici cambiano.

---

## 📦 6. Dati e script

📌 Qui ci sono solo i **risultati**: analisi, file Excel e dashboard.

📥 I dati si possono riscaricare dalle fonti (link più sotto).

🐍 Gli script Python di raccolta e pulizia dei dati sono disponibili su richiesta.

---

## ⚠️ 7. Limiti

📌 Redditi **lordi** e **medi**: le persone molto ricche alzano la media.

📌 Prezzi delle case medi per **tutta la provincia**: in città e al mare costano di più.

📌 Mancano **affitti**, bollette e spesa: è un costo della vita "parziale".

📌 La benzina è di **un solo giorno** (15 ottobre 2026).

📌 **Sud Sardegna** non ha il prezzo delle case.

---

## 🔗 8. Da dove arrivano i dati (link)

| Fonte | Cosa ho preso | Link |
|---|---|---|
| MEF – Dichiarazioni dei redditi (open data) | Redditi IRPEF per comune, anni d'imposta 2016-2024 | https://www1.finanze.gov.it/finanze/analisi_stat/public/index.php?opendata=yes |
| Agenzia delle Entrate – OMI | La fonte ufficiale delle quotazioni immobiliari | https://www.agenziaentrate.gov.it/portale/web/guest/schede/fabbricatiterreni/omi/banche-dati/quotazioni-immobiliari |
| GitHub "eugeniodalpozzo/italy_omi_housing_provincial_prices" | I prezzi OMI già raccolti per zona, usati da `01_scarica.py` | https://github.com/eugeniodalpozzo/italy_omi_housing_provincial_prices |
| MIMIT – Prezzi carburanti | Benzina self per provincia (dal mio progetto Carburanti) | https://www.mimit.gov.it/it/open-data/elenco-dataset/carburanti-prezzi-praticati-e-anagrafica-degli-impianti |
| ISTAT – Indice NIC (tramite Rivaluta.it) | Inflazione 2016-2024: +20,9% | https://rivaluta.istat.it/ |

📅 Dati scaricati il **27 ottobre 2026**.

⚖️ Dati pubblici di MEF, Agenzia delle Entrate, MIMIT e ISTAT.

---

## 🪜 9. Tutti i passaggi fatti, in ordine

1️⃣ **Scelta del progetto**: un tema che riguarda tutti, unendo 3 fonti ufficiali.

2️⃣ **Domande**: ho fissato le 5 domande.

3️⃣ **Raccolta** (`01_scarica.py`): 9 zip dei redditi dal sito del MEF, prezzi OMI da GitHub, benzina dal progetto Carburanti.

4️⃣ **Controllo**: "NA" letto come vuoto, colonne spostate nei file MEF, redditi negativi, valori OMI impossibili.

5️⃣ **Pulizia** (`02_pulizia.py`): medie per provincia, valori sbagliati tolti, anni mancanti riempiti.

6️⃣ **Indicatori**: casa da 80 m², anni di reddito, peso del pieno, indice del costo della vita.

7️⃣ **Python**: notebook con 9 grafici, correlazione di Spearman e confronto con l'inflazione.

8️⃣ **Excel**: 10 fogli con formule (929), confronto tra 2 province e calcolatore, 0 errori.

9️⃣ **Power BI**: dashboard di 5 pagine con mappa e pulsanti per zona, aperta e controllata in Power BI Desktop.

🔟 **PDF e conclusioni**: esportata la dashboard e scritte le risposte alle domande.
