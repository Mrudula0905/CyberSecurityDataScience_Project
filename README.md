# CyberSecurity Data Science Project

Deep learning-based vulnerability detection for Java source code using real-world CVE fixing commits. This project builds an end-to-end pipeline that automatically collects vulnerable code samples, trains neural network models, and predicts whether a Java function is vulnerable.

## Project Overview

The project consists of two main stages:

1. **Data Collection & Preprocessing**
   - Mine vulnerability-fixing commits from SAP ProjectKB.
   - Clone affected GitHub repositories.
   - Extract modified Java methods using PyDriller.
   - Generate vulnerable and safe function samples.
   - Remove duplicate methods and prepare the final dataset.

2. **Model Training & Evaluation**
   - Tokenize Java source code.
   - Train three deep learning models:
     - BiLSTM (Baseline)
     - BiLSTM (Larger)
     - BiGRU
   - Combine predictions using an ensemble.
   - Tune the decision threshold to maximize the F1 score.
   - Generate predictions for the challenge dataset.

---

## Repository Structure

```
.
├── CDS_Part2_Data_Collection.ipynb      # Dataset collection & preprocessing
├── CDS_Part3_Training&Evaluation.ipynb  # Model training, evaluation & inference
├── CDS_PBL_Report.pdf/.docx             # Project report
└── README.md
```

---

## Dataset

The dataset is built from **SAP ProjectKB**, which links Common Vulnerabilities and Exposures (CVEs) to their corresponding security-fixing commits in open-source Java projects.

The pipeline:

- Parses ProjectKB vulnerability metadata
- Downloads affected repositories
- Extracts modified Java methods
- Labels vulnerable and safe functions
- Removes duplicate samples
- Exports a training-ready dataset

---

## Model Architecture

The final system uses an ensemble of three recurrent neural networks:

| Model | Description |
|--------|-------------|
| BiLSTM | Baseline bidirectional LSTM |
| BiLSTM (Large) | Deeper and wider BiLSTM |
| BiGRU | Bidirectional GRU model |

Each model learns token embeddings directly from Java source code, and the final prediction is obtained by averaging their outputs.

---

## Technologies Used

- Python
- PyTorch
- PyDriller
- Pandas
- NumPy
- Scikit-learn
- Google Colab

---

## Results

The final ensemble achieved the best performance after threshold tuning:

- **F1 Score:** **55.4%**
- **Recall:** **72.0%**
- **Precision:** **45.0%**
- **Leaderboard Rank:** **#3**

<img width="2084" height="731" alt="loss_curves" src="https://github.com/user-attachments/assets/c75e42e0-9d1a-45e4-a54e-5b5530ee0370" />

<img width="860" height="732" alt="confusion_matrix" src="https://github.com/user-attachments/assets/c0848337-4623-480c-bb2f-8655c85ca19a" />


---

## How to Run

### 1. Data Collection

Run:

```
CDS_Part2_Data_Collection.ipynb
```

This notebook:

- Downloads ProjectKB
- Collects vulnerability data
- Extracts Java methods
- Creates the final dataset

### 2. Model Training

Run:

```
CDS_Part3_Training&Evaluation.ipynb
```

This notebook:

- Loads the processed dataset
- Trains the three neural networks
- Performs ensemble prediction
- Evaluates performance
- Produces challenge predictions

---

## Authors

- **Mrudula Sachin Rothe**
- **Ayush Prakash Parab**

---

## License

This repository was developed as part of the **CyberSecurity Data Science** course project at Hamburg University of Technology (TUHH).
