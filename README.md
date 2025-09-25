[README.md](https://github.com/user-attachments/files/22534078/README.md)
# Dal Datalake alla Clinical Decision  
**Architetture Cloud per una Governance Efficace dei Dati Sanitari**

## 📌 Descrizione del progetto
Questo repository contiene il codice e i materiali di supporto alla tesi magistrale:  
**"Dal Datalake alla Clinical Decision: Architetture Cloud per una Governance Efficace dei Dati Sanitari"**,  
svolta presso l’Università degli Studi Guglielmo Marconi (A.A. 2024/2025).

L’obiettivo è progettare e validare una **pipeline data-driven** basata su tecniche di cloud computing e machine learning, capace di supportare il processo diagnostico clinico tramite:
- un **modulo predittivo** (Random Forest, XGBoost) per stimare la probabilità di malattia cardiovascolare;  
- un **modulo di similarità** che confronta un paziente con casi già osservati, fornendo contesto clinico interpretativo.

## 📊 Dataset di riferimento
Il progetto utilizza il dataset:  
**Heart Disease Health Indicators – BRFSS 2015**  
- Fonte: [Kaggle – Heart Disease Health Indicators Dataset](https://www.kaggle.com/datasets/alexteboul/heart-disease-health-indicators-dataset)  
- Osservazioni: > 400.000  
- Variabili: indicatori clinici, comportamentali e sociodemografici (binari e numerici).  
- Variabile target: presenza/assenza di malattia cardiovascolare.

## 🏗️ Architettura della pipeline
La pipeline è composta da più fasi:

1. **Raccolta e ingestion dei dati**  
   Caricamento del dataset e validazione (assenza di missing values, tipi di variabili).  
2. **Pre-processing**  
   - Train/test split  
   - Standardizzazione (BMI)  
   - Encoding variabili categoriche  
   - Verifica varianza  
   - Oversampling con **SMOTE**  
   - Salvataggio artefatti (CSV, scaler, features list).  
3. **Modulo Predittivo**  
   - **Random Forest**: ricerca iperparametri, valutazione metriche, interpretabilità (feature importances).  
   - **XGBoost**: ottimizzazione, scelta soglia robusta, confronto performance.  
4. **Modulo di Similarità (KNN)**  
   - Normalizzazione features  
   - Calcolo indici KNN  
   - Analisi caso singolo + batch di pazienti  
   - Output: CSV e JSON con analisi di similarità.  
5. **Output della pipeline**  
   - Metriche di valutazione (precision, recall, ROC/PR curve)  
   - Report di interpretabilità  
   - Artefatti salvati per riuso.

## ⚙️ Istruzioni di esecuzione

### 🔹 Esecuzione su Google Colab
1. Apri il notebook `Appendice_Codice_Finale_structured.ipynb` in Colab.  
2. Esegui le celle di setup (`!pip install ...`).  
3. Scarica il dataset da Kaggle e caricalo nel notebook (es. tramite `files.upload()`).  
4. Procedi sezione per sezione:  
   - Pre-processing → Random Forest → XGBoost → Modulo di Similarità.  
5. Verifica gli artefatti prodotti nelle cartelle `./artifacts/`.

### 🔹 Esecuzione locale
1. Clona il repository:  
   ```bash
   git clone https://github.com/NicMangia96/Dal-Datalake-alla-clinical-decision.git
   cd Dal-Datalake-alla-clinical-decision
   ```  
2. Crea un ambiente virtuale:  
   ```bash
   python -m venv venv
   source venv/bin/activate  # su Windows: venv\Scripts\activate
   ```  
3. Installa le dipendenze:  
   ```bash
   pip install -r requirements.txt
   ```  
4. Avvia Jupyter:  
   ```bash
   jupyter notebook
   ```  
5. Apri `Appendice_Codice_Finale_structured.ipynb` e segui le sezioni.

## 📈 Risultati principali
- **Random Forest** e **XGBoost** hanno mostrato buone performance predittive, con recall migliorabile su classi minoritarie.  
- Il **modulo di similarità** ha permesso di interpretare i risultati, collegando i pazienti analizzati a cluster di casi storici.  
- La pipeline dimostra la fattibilità di un **Clinical Decision Support System (CDSS)** cloud-based, utile come strumento di supporto (non sostitutivo) all’attività clinica.

## 🔮 Prospettive future
- Integrazione con dati clinici reali (EHR, immagini mediche).  
- Deploy su piattaforme cloud-native (es. GCP Healthcare API, AWS HealthLake).  
- Adozione di tecniche di explainable AI (SHAP, LIME).  
- Estensione ad altre patologie croniche.

## 📚 Riferimenti
- Tesi di laurea magistrale: *Dal Datalake alla Clinical Decision: Architetture Cloud per una Governance Efficace dei Dati Sanitari* (Università Guglielmo Marconi, A.A. 2024/2025).  
- Dataset: [Kaggle – Heart Disease Health Indicators](https://www.kaggle.com/datasets/alexteboul/heart-disease-health-indicators-dataset).  
- Documentazione Scikit-learn, XGBoost, Imbalanced-learn.  
