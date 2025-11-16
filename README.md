AltRAG+: Retrieval-Augmented Graphs for Dynamic Mortality Trajectories

This repository contains the implementation of AltRAG+, a retrieval-augmented clinical decision-support system designed for ICU patients using MIMIC-IV.

AltRAG+ integrates:

Structured EHR processing (MIMIC-IV)

Graph construction using NetworkX

Graph storage & querying using Neo4j

Semantic patient retrieval using SBERT + FAISS

Causal modeling with IPTW-weighted Cox PH

ML prediction models (Logistic Regression, XGBoost, LSTM)

LLM-based biomedical embeddings (BioGPT prototype)

The goal is to identify similar past ICU patients, analyze their treatment pathways, and generate K alternative, clinically-equivalent treatment strategies with predicted outcomes.
AltRAG-Plus/
├── Group9_Capstone.ipynb     # Main notebook (end-to-end workflow)
├── INFO 5082 Final PPT.pptx  # Final presentation
├── flowchart.png             # Workflow diagram
├── README.md
└── .gitignore
Key Features
1. Data Integration & Preprocessing

Combined 7+ MIMIC-IV tables

Added vitals, labs, treatment intensity features

Handled missing values (median, domain-based rules)

2. Graph Construction

Created heterogeneous graph:

Patients (50920 nodes)

Diagnoses (16k)

Drugs (1423)

Procedures (146)

Exported to CSV and stored in Neo4j

3. Patient Retrieval (SBERT + FAISS)

Encoded patient profiles

Built FAISS ANN index (~73k vectors)

Retrieved top-K similar “digital twins”

4. Causal Modeling & Counterfactuals

IPTW weighting

High vs low treatment intensity

Cox PH survival comparison

5. Prediction Models

Logistic Regression (AUC ~0.83)

XGBoost (AUC 0.87)

LSTM Time-Series model (Accuracy 0.910)

6. Treatment Recommendation Engine

For a new ICU patient:

Encode profile

Retrieve similar historical patients

Extract treatment subgraphs from Neo4j

Predict mortality trajectory using LSTM

Generate alternative treatment paths
How to Reproduce

To reproduce this work:

Request MIMIC-IV access from PhysioNet.

Download the dataset locally.

Update paths inside the notebook.

Install dependencies (PyTorch, Sentence-Transformers, FAISS, Neo4j, scikit-learn, xgboost, lifelines, tensorflow).


If referencing this project:

Rajesh Sathuri et al., “AltRAG+: Retrieval-Augmented Graphs for Dynamic Mortality Trajectories,” UNT Graduate Capstone, 2025.
