---
layout: "../../layouts/post.astro"  
title: "Day 1: An Introduction to Hugging Face"
description: "A starting point for your journey with Hugging Face, covering its features and capabilities, and how to get started."
dateFormatted: "March 19, 2025"  
tags: ["Hugging Face", "AI", "Introduction", "Tutorial"]
---

# Getting Started with Hugging Face in Python

This tutorial will introduce you to the Hugging Face ecosystem, focusing on the [Transformers](https://huggingface.co/transformers/) library. We’ll cover setting up your environment, installing the necessary libraries, and running your very first example using a pre-trained model.

---

## 1. Introduction

Hugging Face is a popular open‐source platform that provides pre-trained models for Natural Language Processing (NLP), computer vision, speech tasks, and more. Their flagship library, Transformers, makes it simple to use state-of-the-art models like BERT, GPT-2, and DistilBERT without having to train from scratch.

---

## 2. Prerequisites

Before you begin, ensure you have:
- **Python 3.8+** installed on your system.
- Basic familiarity with Python programming.
- A code editor or IDE (e.g., Visual Studio Code or Jupyter Notebook).

---

## 3. Setting Up Your Environment

### Option A: Using a Virtual Environment

1. **Create a Project Folder**  
   Open your terminal and create a new directory:
   ```bash
   mkdir huggingface-tutorial
   cd huggingface-tutorial
   ```

2. **Create and Activate a Virtual Environment**
   ```bash
   python -m venv venv
   # On Unix/macOS:
   source venv/bin/activate
   # On Windows:
   venv\Scripts\activate
   ```

3. **Install Required Libraries**
   Use pip to install the Transformers library along with additional packages:
   ```bash
   pip install transformers
   pip install tokenizers datasets  # Optional but useful for many projects
   ```

### Option B: Using Google Colab

If you prefer an online environment:
1. Open [Google Colab](https://colab.research.google.com/#create=true).
2. In a new notebook, install Transformers by running:
   ```python
   !pip install transformers[sentencepiece]
   ```
3. Import the library to verify the installation:
   ```python
   import transformers
   print(transformers.__version__)
   ```


---

## 4. Your First Hugging Face Example: Sentiment Analysis

We will create a simple script that uses a pre-trained model for sentiment analysis. In this example, we’ll use the DistilBERT model fine-tuned on the SST-2 dataset.

### Step 4.1: Import Libraries and Load the Pipeline

Create a new Python script (e.g., `sentiment_analysis.py`) and add the following code:
```python
from transformers import pipeline

# Load the sentiment-analysis pipeline using a pre-trained model
sentiment_analyzer = pipeline("sentiment-analysis",
                              model="distilbert-base-uncased-finetuned-sst-2-english")

# Example text for sentiment analysis
texts = [
    "I absolutely love using Hugging Face libraries!",
    "The experience was really disappointing and poor."
]

# Analyze the sentiments of the texts
results = sentiment_analyzer(texts)

# Print out the results
for text, result in zip(texts, results):
    print(f"Text: {text}")
    print(f"Sentiment: {result['label']} with confidence {result['score']:.2f}\n")
```

### Step 4.2: Run Your Script

If you’re using a virtual environment, run your script from the terminal:
```bash
python sentiment_analysis.py
```
You should see output similar to:
```
Text: I absolutely love using Hugging Face libraries!
Sentiment: POSITIVE with confidence 0.99

Text: The experience was really disappointing and poor.
Sentiment: NEGATIVE with confidence 0.99
```

---

## 5. Exploring More with Hugging Face

After you get comfortable with sentiment analysis, consider exploring other pipelines such as:

- **Text Generation:** Use any LLM to generate text.
- **Named Entity Recognition (NER):** Identify entities within your text.
- **Question Answering:** Use models like `deepset/roberta-base-squad2` to build Q&A applications.
- **Translation:** Translate text between languages.

Each pipeline follows a similar pattern: load the pipeline, provide your input, and process the output.

For instance, a quick snippet for question answering:
```python
from transformers import pipeline

qa_pipeline = pipeline("question-answering", model="deepset/roberta-base-squad2")

context = "Hugging Face is a company that provides state-of-the-art machine learning models and tools."
question = "What does Hugging Face provide?"

result = qa_pipeline(question=question, context=context)
print(result)
```

---

## 6. In the End

This tutorial introduced you to the basics of using Hugging Face with Python. You learned how to set up your environment, install the Transformers library, and build a simple sentiment analysis application using a pre-trained model. As you continue exploring, you’ll discover that Hugging Face’s extensive model hub and easy-to-use pipelines empower you to implement advanced NLP, vision, and speech applications with minimal code.

Happy coding and enjoy exploring the world of Hugging Face!
