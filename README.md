Uncertainty-Aware Classification of Medical Text
Overview

This project investigates uncertainty-aware machine learning for medical text classification, focusing on the reliability of probabilistic predictions in a clinical context.

Using a dataset of medical abstracts across five disease categories, the study goes beyond classification accuracy to analyze:

- Prediction confidence
- Model calibration
- Reliability of probabilistic outputs

Motivation

In healthcare applications, incorrect predictions with high confidence can lead to serious consequences. Therefore, machine learning systems must not only be accurate but also well-calibrated and uncertainty-aware.

This project explores whether model confidence can be used as a proxy for prediction reliability, and how calibration techniques can improve this relationship.

Methodology

1. Dataset
   ~14,000 training samples of medical abstracts
   5 disease categories:
   - Digestive system diseases
   - Cardiovascular diseases
   - Neoplasms
   - Nervous system diseases
   - General pathological conditions
   - Data Source: Kaggle

2. Text Representation
   TF-IDF vectorization
   Unigrams and bigrams (Both unigrams (individual words) and bigrams (two-word phrases) were used to capture not only individual terms but also clinically meaningful expressions such as 'prostate cancer')
   Preprocessing of unstructured clinical text

3. Model
   Linear classifier trained using stochastic gradient descent
   Probabilistic outputs via logistic loss

Evaluation

- Baseline Performance
- Accuracy: ~61%

While performance is moderate, the focus of this work is on uncertainty and reliability, rather than maximizing accuracy.

Uncertainty Quantification

- Prediction probabilities were used as confidence scores
- Maximum predicted probability represents model confidence
- Confidence values were analyzed against prediction correctness

Key Observation

Predictions with lower confidence are significantly more error-prone, indicating that confidence is a meaningful proxy for uncertainty.

Calibration Analysis

A calibration curve was used to evaluate how well predicted probabilities reflect true correctness likelihood.

Findings (Before Calibration)
The model exhibited systematic underconfidence
Predictions were often more accurate than their assigned probabilities suggested
Calibration Approach
Applied Platt scaling using sigmoid calibration
Results (After Calibration)

- Calibration improved alignment with the ideal diagonal
- Several probability bins moved closer to perfect calibration
- However, mild underconfidence persists, especially at higher confidence levels

Interpretation
The persistence of slight underconfidence suggests:

- The model is conservative in its probability estimates
- Raw probabilities may underestimate true correctness likelihood
- Even after calibration, uncertainty estimation remains imperfect

This highlights the importance of:

- post-hoc calibration methods
- more advanced probabilistic modeling approaches

Clinical Relevance
This project demonstrates a simplified framework for:

- Identifying unreliable predictions
- Filtering decisions based on confidence thresholds
- Improving safety through selective prediction

Such approaches are critical in clinical AI systems where decision reliability is as important as accuracy.

Future Work

- Bayesian neural networks for principled uncertainty estimation
- Monte Carlo dropout for approximate Bayesian inference
- Ensemble methods for epistemic uncertainty
- Integration with time-to-event models in clinical research
- Application to large language models (LLMs) in medical NLP

Tech Stack

- Python
- scikit-learn
- NumPy / Pandas
- Matplotlib

Key Summary
This study shows that even simple models can provide meaningful uncertainty estimates, but careful calibration is necessary to ensure their reliability in high-stakes applications such as healthcare.
