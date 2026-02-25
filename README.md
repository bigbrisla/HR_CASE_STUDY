# HR Analytics: Previsione e Analisi del Turnover Aziendale (Attrition)

## 📌 Descrizione del Progetto
Questo progetto applica tecniche di Machine Learning e Explainable AI (XAI) per analizzare e prevedere il turnover dei dipendenti (attrition) all'interno di una grande azienda (XYZ) che impiega circa 4000 dipendenti[cite: 3]. L'azienda registra un tasso di turnover annuale critico del 15%[cite: 4, 33]. L'obiettivo principale è modellare la probabilità di turnover [cite: 19] e identificare i fattori lavorativi, organizzativi e personali che influenzano maggiormente la decisione dei dipendenti di lasciare l'azienda, così da poter intervenire in maniera mirata[cite: 15].

## 🎯 Obiettivi di Business
* **Comprendere le cause:** Analizzare in modo sistematico i fattori che guidano il turnover[cite: 14].
* **Definire strategie:** Migliorare la soddisfazione, il coinvolgimento e la fidelizzazione dei dipendenti nel medio-lungo periodo[cite: 16].
* **Allocare risorse:** Individuare le variabili più urgenti su cui agire per ottenere benefici concreti nel minor tempo possibile[cite: 17].

## 📊 Dataset e Feature Engineering
Il dataset iniziale è stato aggregato partendo da cinque fonti distinte: dati anagrafici, survey sui dipendenti, survey sui manager e log temporali di ingresso/uscita[cite: 71].

Per arricchire il dataset e catturare le dinamiche comportamentali, è stata eseguita una fase avanzata di **Feature Engineering** sui file grezzi di Time Tracking[cite: 78]:
* `HoursPerDay` (Intensità lavorativa): Media delle ore lavorate calcolata dalla differenza tra orario di uscita e ingresso[cite: 80].
* `LongestAbsence` (Discontinuità): Numero massimo di giorni consecutivi di assenza per intercettare il disimpegno[cite: 81, 82].
* `WorkOffHours` (Disallineamento orario): Frequenza con cui un dipendente inizia o termina il turno in orari anomali, per rilevare potenziale stress da straordinari[cite: 83, 84].

## 🧠 Metodologia e Modelli
Il problema è stato affrontato come un task di classificazione binaria[cite: 40]. A causa della natura sbilanciata del problema, la valutazione si è basata su Precision, Recall, F1-Score e l'area sotto la curva ROC (AUC-ROC), oltre all'Accuracy[cite: 91, 121, 122].

Sono stati addestrati e confrontati sei algoritmi[cite: 90]:
* Logistic Regression (modello di riferimento) [cite: 20]
* Support Vector Machine (SVM) [cite: 90]
* K-Nearest Neighbors (KNN) [cite: 90]
* Decision Tree [cite: 90]
* Random Forest [cite: 90]
* XGBoost [cite: 90]

## 🏆 Risultati Principali
* **Migliori Modelli:** Random Forest e XGBoost hanno ottenuto le prestazioni migliori in assoluto, con un'accuratezza prossima al 98-99% e un F1-Score molto elevato, minimizzando sia i falsi positivi che i falsi negativi[cite: 125, 126].
* **Interpretabilità (SHAP):** Per superare il limite della "Black Box", è stata applicata l'analisi SHAP[cite: 24, 48, 149]. Sono emersi insight operativi molto chiari:
  1. **Burnout:** All'aumentare delle ore medie lavorate (`HoursPerDay`), aumenta drasticamente la probabilità di abbandono[cite: 179, 180, 181]. Questo carico di lavoro è uno dei predittori più forti, spesso superiore alle variabili anagrafiche classiche[cite: 191, 192].
  2. **Demografia:** I dipendenti più giovani (`Age`) e con meno esperienza (`TotalWorkingYears`) sono i più volatili e propensi a lasciare l'azienda[cite: 182, 183].
  3. **Leadership:** Relazioni brevi con il manager corrente (`YearsWithCurrManager`) sono associate a un rischio maggiore, evidenziando l'importanza della stabilità relazionale[cite: 184]. Al contrario, le assenze prolungate (`LongestAbsence`) si sono rivelate marginali se giustificate[cite: 131, 132].

## 🚀 Sviluppi Futuri
* **Analisi Time-Series (Survival Analysis):** Per stimare non solo se, ma quando un dipendente lascerà l'azienda[cite: 203].
* **Analisi testuale (NLP):** Integrare dati non strutturati (es. commenti liberi o interviste di uscita) per catturare il "sentiment" qualitativo[cite: 204].
* **Deployment:** Sviluppare una dashboard interattiva per l'ufficio HR che segnali in tempo reale i dipendenti a rischio per interventi proattivi[cite: 205].
