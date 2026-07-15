# Can Large Language Models interpret participatory mapping comments at scale? Evidence from Prague’s emotional mapping

## Overall intro & scope
This repository contains the data, inference code (including prompts), and results necessary to reproduce the findings for Agile 2026 conference paper. This work proposes an exploratory benchmark method for analysing participatory data using Large Language Models (LLMs). We focus on two main tasks: (1) **sentiment analysis**, to process emotions expressed in citizen comments, and (2) **thematic analysis**, to categorise unstructured citizen feedback into predefined participatory mapping categories.

## Requirements
The analysis scripts and data processing were run using Python version 3.13.9. The repository provides the raw data, ground truth labels, and all LLM prompts used for inference. For full local reproduction of the LLM inferences, a workstation similar to ours is recommended: an Intel Core i9-14900K CPU (24 cores), 96 GB RAM, and an NVIDIA GeForce RTX 4090 GPU, running Ubuntu 22.04.5 LTS. **Note that setting up Ollama and downloading the specific LLM models (e.g., DeepSeek-R1-0528-Qwen3-8B) is also required.**

## Repository structure organisation
### Data folder contains:
- "Prague_emotional_data", the complete dataset of the participatory mapping exercise that occurred in Prague in 2021 as `.geojson` file ([DOI: 10.17632/bmzwzwcw9w.1](https://doi.org/10.17632/bmzwzwcw9w.1)).
- "prague_emotional_data", the subset used for the sumbitted work as `.xlsx` file.

### Inference folder contains:
- "nlp_inference_sentiment", the **NLP sentiment analysis (Hugging Face)** as `.ipynb` file: automatically classifies the sentiment (positive, negative, or neutral) of citizen comments using a Hugging Face RoBERTa model.
- "llm_inference_sentiment", the **LLM sentiment analysis (Ollama)** as `.ipynb` file: automatically classifies the sentiment (positive, negative, or neutral) of citizen comments in both English and Czech. This workflow uses local LLMs via Ollama (e.g., DeepSeek-R1-0528-Qwen3-8B, Gemma3:12b, OpenEuroLLM-Czech:12b) and provides a detailed reasoning for each prediction, alongside a confidence score and the prompts used.
- "llm_inference_thematic", the **LLM thematic analysis (Ollama)**: automatically categorizes citizen comments into eight predefined participatory mapping categories in both English and Czech, providing detailed reasoning and confidence scores for each classification, using a local LLM (DeepSeek-R1-0528-Qwen3-8B) via Ollama.

### Results folder contains all visualisations & figures featured in the paper provided as `.pdf` files. Specifically:  
- the accuracy comparisons of different LLMs.
- the comments density in Prague districts.
- the confidence threshold and comments dropped per task and model.
- the confusion matrices. 

## Note on reproducibility
To account for the stochastic nature of LLM decoding, all inference runs were repeated five times. Please note that Large Language Models are inherently non-deterministic, and re-processing the same dataset may lead to slightly different results.

