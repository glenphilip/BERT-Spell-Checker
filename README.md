# BERT-Based Spell Checker

A deep-learning spell checker that uses **BERT token classification** for error detection and **BERT masked language modeling** for context-aware correction—optimized for real-time feedback in a web UI.

---

## 🎯 Overview

This system goes beyond dictionary lookups by leveraging BERT’s bidirectional context. It:

- **Detects** likely issues using a fine-tuned token classifier.
- **Corrects** them by masking flagged tokens and decoding with a masked language model (MLM).
- Handles **homophones**, **grammar/verb tense**, **context-dependent** issues, and **real-word** errors.

---

## 🚀 Key Features

- **Dual-Model Architecture:** Dedicated detector and corrector
- **Context-Aware Corrections:** Bidirectional semantics from BERT
- **Real-Time Processing:** Latency-optimized pipeline for web use
- **PEFT with LoRA:** Large parameter savings while retaining performance
- **Clean Web UI:** Flask backend with responsive frontend

---

## 🧠 Technical Architecture

### Error Detection (Token Classification)

- **Model:** `BertForTokenClassification`
- **Labels:** `CORRECT`, `INCORRECT`
- **Training:** Freeze select layers; adapt heads with LoRA
- **Objective:** Binary token-level classification

### Error Correction (Masked LM)

- **Model:** `BertForMaskedLM`
- **Approach:** Replace detected error tokens with `[MASK]`
- **Selection:** Choose the most probable replacement
- **Goal:** Preserve semantic and syntactic coherence

### PEFT / LoRA

- **Method:** Low-Rank Adaptation applied to attention blocks
- **Effect:** Train only lightweight adapters while keeping the base model fixed

---

## 🧰 Tech Stack

- **Core:** PyTorch, Hugging Face Transformers
- **Base Model:** `google-bert/bert-base-cased`
- **PEFT:** `peft` (LoRA)
- **Backend:** Flask (+ optional ngrok)
- **Frontend:** HTML, CSS, JavaScript
- **Data/Utils:** `pandas`, `NLTK`, `datasets`, `evaluate`, `seqeval`, `tqdm`, `contractions`, `pattern`

---

## 📂 Project Structure

