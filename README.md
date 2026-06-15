# Edge-IIoTset Intrusion Detection — AI and Cyber Final Project

**Course:** AI and Cyber — Sourav Rai
**Track:** A — Dataset project
**Team:** Ibrahim Hamed DICKO, Mariam ARKIK, Abdoulaye TOURE

---

## 1. Dataset

**Edge-IIoTset — A New Comprehensive Realistic Cyber Security Dataset of IoT and IIoT
Applications for Centralized and Federated Learning**

- Source: https://www.kaggle.com/datasets/mohamedamineferrag/edgeiiotset-cyber-security-dataset-of-iot-iiot
- Paper: Ferrag, M.A., Friha, O., Hamouda, D., Maglaras, L., Janicke, H. — *IEEE Access*,
  April 2022, DOI: 10.1109/ACCESS.2022.3165809
- File used: `DNN-EdgeIIoT-dataset.csv` (raw: 2,219,201 rows × 63 columns)
- Targets: `Attack_label` (binary) and `Attack_type` (multiclass, 15 classes: Normal + 14
  attack types across 5 categories — DoS/DDoS, Information Gathering, MITM, Injection, Malware)

### ⚠️ Data is NOT committed to this repo

The raw file is too large (~hundreds of MB) for git. Each team member must:

1. Download the raw CSV via Kaggle CLI (see notebook Section 1)
2. Run the **stratified 10% sampling cell** (fixed `random_state=42`) to produce
   `data/DNN-EdgeIIoT-sample10.csv` locally — identical for everyone thanks to the fixed seed

Both `data/raw/` and `data/*.csv` are git-ignored.

## 2. Project structure

```
.
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/                          (gitignored — full Kaggle download)
│   └── DNN-EdgeIIoT-sample10.csv     (gitignored — regenerate locally, seed=42)
└── notebooks/
    └── 01_final_project_edgeiiot.ipynb
```

## 3. Setup (local)

```bash
git clone <your-repo-url>
cd <repo-name>

python3 -m venv .venv
source .venv/bin/activate          # fish: source .venv/bin/activate.fish

pip install -r requirements.txt

# Kaggle setup
pip install kaggle
mkdir -p ~/.kaggle && cp /path/to/kaggle.json ~/.kaggle/ && chmod 600 ~/.kaggle/kaggle.json

mkdir -p data/raw
kaggle datasets download -d mohamedamineferrag/edgeiiotset-cyber-security-dataset-of-iot-iiot \
    -f "Edge-IIoTset dataset/Selected dataset for ML and DL/DNN-EdgeIIoT-dataset.csv" \
    -p data/raw --unzip

jupyter notebook notebooks/01_final_project_edgeiiot.ipynb
# Then run the sampling cell ONCE (Section 1, Step 2)
```

## 4. Reproducibility

`RANDOM_STATE = 42` everywhere: stratified sampling, train/test split, cross-validation
folds, model initializations.

## 5. Team workload split (suggested — 3 members)

- **Member 1:** Sections 2 (EDA, full 9 sub-parts)
- **Member 2:** Section 3 (4 models, binary + multiclass)
- **Member 3:** Sections 4–5 (tuning, evaluation, comparison plots)

Each section's markdown questions should be answered by whoever implements that section,
then reviewed together before the presentation.

## 6. Progress tracker

- [x] 1. Data acquisition (domain context, sampling script, loader)
- [ ] 2a–2i. EDA
- [ ] 3. Model development (Logistic Regression, SVM, Decision Tree, Random Forest — binary + multiclass)
- [ ] 4. Hyperparameter tuning
- [ ] 5. Evaluation
- [ ] Presentation slides
