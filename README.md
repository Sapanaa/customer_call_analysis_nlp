# 📞 Customer Call Analysis using NLP & Speech Processing

This project applies **Natural Language Processing (NLP)** and **Speech
Processing** techniques to analyze customer service calls. The pipeline
converts audio to text, extracts linguistic signals, analyzes sentiment,
identifies named entities, measures semantic similarity, and discovers
latent complaint categories using unsupervised learning.

The goal is to demonstrate an **end-to-end NLP system** that mirrors
real-world customer support analytics.

---

## 📂 Dataset

- **Audio**: Sample customer call audio (WAV format)
- **Text**: Customer call transcriptions with sentiment labels
- **Domain**: Customer support complaints (orders, delivery, refunds)

---

## ⚙️ Project Pipeline Overview

1. **Speech-to-Text**
2. **Sentiment Analysis**
3. **Named Entity Recognition (NER)**
4. **Semantic Similarity Search**
5. **Unsupervised Complaint Clustering**

---

## 🎙️ Step 1 — Speech to Text

Customer call audio is converted into text using the
`SpeechRecognition` library with Google’s speech recognition API.

**Audio preprocessing includes:**
- Handling WAV input
- Channel and frame-rate inspection
- Conversion to PCM-compatible format when required

This step simulates real-world call center transcription workflows.

---

## 😊 Step 2 — Sentiment Analysis

Sentiment classification is performed using **VADER**, a rule-based
lexicon model designed for short conversational text.

- Outputs: `positive`, `neutral`, `negative`
- Decision based on compound sentiment score
- Performance evaluated using precision, recall, and F1-score

**Observation:**  
VADER performs reasonably on negative complaints but struggles with
neutral vs. positive ambiguity, highlighting limitations of rule-based
approaches.

---

## 🧍 Step 3 — Named Entity Recognition (NER)

Named entities are extracted using spaCy’s English language model.

- Identifies names, dates, and other entities
- Used to surface frequently referenced entities in calls

**Insight:**  
Temporal terms such as *“yesterday”* appear frequently, reflecting
customer references to recent events rather than specific people or
organizations.

---

## 🔍 Step 4 — Semantic Similarity Search

Two approaches are demonstrated:

### Baseline (spaCy)
- Uses contextual similarity from a lightweight language model
- Limited by lack of pretrained word vectors

### Modern Approach (Transformers)
- Sentence embeddings generated using a transformer-based model
- Cosine similarity used to match user queries (e.g. *“wrong package
  delivery”*) against customer complaints

This enables **semantic search**, not just keyword matching.

---

## 🧠 Step 5 — Unsupervised Complaint Clustering

Customer complaints are grouped using:

- Transformer-based sentence embeddings
- KMeans clustering (unsupervised)

### Discovered Complaint Categories

- **Cluster 0 – Order Status & Shipping**  
  Questions about delivery time and shipment tracking

- **Cluster 1 – Product Issues & Setup**  
  Faulty, damaged products or setup assistance

- **Cluster 2 – Wrong Delivery**  
  Incorrect or mismatched shipments

- **Cluster 3 – Refunds & Returns**  
  Dissatisfaction, wrong size, or refund requests

These clusters were discovered **without labels**, demonstrating the
effectiveness of semantic embeddings for automated issue categorization.

---

## 📊 Evaluation Summary

- Sentiment classification accuracy: ~53%
- Strong performance on negative complaints
- Unsupervised clusters align closely with real customer support workflows

---

## 🧰 Technologies Used

- **Python**
- **SpeechRecognition** (speech-to-text)
- **Pydub** (audio handling)
- **NLTK (VADER)** — sentiment analysis
- **spaCy** — tokenization & NER
- **Sentence Transformers** — semantic embeddings
- **scikit-learn** — clustering & evaluation
- **pandas / NumPy** — data processing

---

## 🚀 Key Takeaways

- Built a full **audio → insight NLP pipeline**
- Demonstrated both **rule-based and transformer-based NLP**
- Applied **unsupervised learning** to discover real-world complaint types
- Produced **actionable business insights** from unstructured data

---

## 📌 Future Improvements

- Replace VADER with a fine-tuned transformer sentiment model
- Visualize clusters using UMAP or PCA
- Automate cluster labeling using keyword extraction
- Deploy as an API for real-time customer support triage
