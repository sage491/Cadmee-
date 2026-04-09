Cadmee+ — Condition-Aware Degradation Modeling & Evaluation Engine
Overview

Cadmee+ is a structured experimentation framework built around the C-MAPSS (Commercial Modular Aero-Propulsion System Simulation) dataset for Remaining Useful Life (RUL) prediction.

Instead of treating RUL prediction as a purely modeling problem, Cadmee+ focuses on:

Systematic evaluation of degradation patterns
Constraint-aware feature refinement
Comparative testing of lightweight vs complex approaches
Interpretable, scalable modeling pipelines

This repository represents a commit history of controlled experiments conducted on C-MAPSS datasets (FD001–FD004), evolving from naive baselines to structured, constraint-aware predictive systems.

Motivation

Most approaches to RUL prediction:

Over-rely on deep learning without justification
Ignore operational context and degradation regimes
Lack reproducibility and structured experimentation

Cadmee+ was built to address this by:

Treating prediction as a decision-support problem, not just regression
Applying constraint-based model simplification
Prioritizing interpretability and deployability over complexity

📂 Dataset

Experiments are conducted on the C-MAPSS dataset, which simulates turbofan engine degradation under multiple operating conditions.

Key Characteristics:
Multiple subsets: FD001, FD002, FD003, FD004
Varying:
Operating conditions
Fault modes
Multivariate time-series sensor data
Ground truth: Remaining Useful Life (RUL)

⚙️ Experimental Framework

Cadmee+ follows a structured pipeline:

1. Data Processing
Normalization per operating condition
Sensor selection (removal of low-variance / noisy signals)
Sequence windowing
2. Feature Engineering
Trend extraction
Rolling statistics
Degradation-sensitive transformations
3. Constraint-Based Refinement

Instead of blindly increasing model complexity:

Removed:

Deep learning architectures (high complexity, low marginal gain)
Real-time streaming pipelines
Automated BI dashboards

Modified:

Predictive modeling → trend-aware regression
Feature engineering → limited to high-impact signals
4. Modeling Approaches Tested
Linear Regression (baseline)
Random Forest Regressor
Gradient Boosting
Lightweight sequence models

Focus was on:

Stability across datasets
Generalization across operating regimes
Interpretability
5. Evaluation Metrics
RMSE (Root Mean Squared Error)
Score function (NASA scoring metric for RUL)
Model robustness across FD datasets

🧠 Key Insights

From multiple experimental iterations:

More features ≠ better prediction
Degradation trends matter more than raw sensor values
Simpler models often outperform deep models when:
Proper preprocessing is applied
Noise is controlled
Operating conditions must be explicitly handled

🏗️ Project Structure
cadmee-plus/
│
├── data/
│   ├── raw/                # C-MAPSS raw datasets
│   ├── processed/          # Cleaned and normalized data
│
├── experiments/
│   ├── exp_v1_baseline/
│   ├── exp_v2_feature_refinement/
│   ├── exp_v3_constraint_model/
│
├── models/
│   ├── regression/
│   ├── ensemble/
│
├── utils/
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── evaluation.py
│
├── results/
│   ├── metrics/
│   ├── plots/
│
└── README.md
                
🚀 How to Run

# Clone repo
git clone https://github.com/yourusername/cadmee-plus.git

# Install dependencies
pip install -r requirements.txt

# Run experiment
python experiments/exp_v2_feature_refinement/run.py

📊 Results Summary

Model	RMSE	Notes
Linear Regression	High	Weak baseline
Random Forest	Medium	Good stability
Gradient Boosting	Low	Best performance overall
Deep Models	Variable	High cost, inconsistent gain
🔍 Positioning of Cadmee+

Cadmee+ is not just:

A machine learning project
A dataset experiment

It is a step toward:

                
Context-aware decision systems for engineering environments

This aligns with broader goals of:

Human-in-the-loop systems
Interpretable AI
Engineering reliability frameworks

🔗 Future Work
Integration with real-time maintenance systems
Hybrid physics + data-driven models
Extension to other industrial datasets
Decision-support layer (beyond prediction)

👤 Author

Harshit Kumar

Engineering Student, Chandigarh University
Focus: AI Systems, Decision Frameworks, Applied Intelligence
⚠️ Final Note

Cadmee+ intentionally avoids unnecessary complexity.

The goal is not to build the most complex model —
but to understand what actually works, why it works, and where it fails.
