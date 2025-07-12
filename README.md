# 25-2-R-13 — Literature Sources Analysis Using Deep Impostor Approach
This project presents a fully unsupervised pipeline for detecting stylistic boundaries 
within long or composite texts, a growing challenge in the age of multi-authored, edited,
or compiled documents.

Project Overview  
Building upon the Deep Impostors framework introduced by Dr. Renata Avros and Prof. Zeev Volkovich,  
we utilize deep neural models (CNNs and BERT) to convert textual segments into chunk-level stylistic  
signals. Our core innovation lies in a robust changepoint detection method that enables fine-grained  
segmentation without any labeled data.

Methodology Summary  
1. Text Segmentation:  
   Each document is split into fixed-size batches and grouped into chunks.

2. Word Embedding:  
   Batches are embedded using either:  
   a. Word2Vec (Skip-Gram) — efficient, static lexical vectors  
   b. BERT — contextualized, deep transformer-based embeddings

3. Classifier Training (Deep Impostors):  
   For each unrelated impostor pair, a binary classifier is trained to capture their stylistic  
   contrast.

4. Signal Generation:  
   The trained classifier is applied to the target text, producing a 1D signal of probabilistic  
   stylistic alignment per chunk.

5. Rolling Distance Analysis:  
   A squared difference function is used to detect abrupt local deviations in the stylistic  
   signal — candidate changepoints.

6. Wavelet-Based Refinement:  
   Discrete Wavelet Transform enhances changepoint sensitivity and robustness across scales.

7. Consensus Voting:  
   Aggregates peak locations across all impostor pairs. Only positions agreed upon by a majority  
   are finalized as changepoints.

Technical Implementation  
   a. Language: Python 3.10+  
   b. Libraries: TensorFlow, Scikit-learn, Gensim, NLTK, NumPy, SciPy, Matplotlib  
   c. Models: CNN–BiLSTM, BERT  
   d. Changepoint Detection: Rolling distance + Wavelet + Voting

Evaluation Plan  
   We will evaluate the system against synthetic and annotated datasets with known boundaries.  
   Metrics include:  
   a. Precision: Correctly predicted boundaries  
   b. Recall: Correctly found true boundaries  
   c. F1 Score: Harmonic mean of precision and recall  
      A margin of error (±1 chunk) is allowed in scoring.

Goal  
To demonstrate that combining:  
   a. Deep impostor-based classification  
   b. Rolling stylistic distance analysis  
   c. Signal aggregation via consensus voting  
enables high-precision stylistic segmentation, entirely unsupervised and interpretable.
