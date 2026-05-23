# DistilGPT_Fine_Tuning_Retail_-_E_commerce.ipynb

# Retail & E-commerce AI Chatbot(ShopBot)

This project demonstrates the fine-tuning of a **DistilGPT-2** model to create a specialized AI chatbot for the retail and e-commerce sector. The model is trained to recognize customer sentiment from product reviews and provide appropriate, automated customer service responses.

## Overview

The "ShopBot" is designed to act as a first-line customer support agent. By leveraging the `amazon_polarity` dataset, the model learns to:

1.  Analyze user reviews.
2.  Differentiate between positive and negative feedback.
3.  Generate empathetic and brand-consistent responses.

##  Features

  * **Dataset Integration:** Uses the [Amazon Polarity](https://www.google.com/search?q=https://huggingface.co/datasets/amazon_polarity) dataset for sentiment-aware training.
  * **Fine-Tuning:** Custom training loop using the Hugging Face `Trainer` API with `distilgpt2`.
  * **Optimized Performance:** Uses a distilled version of GPT-2 for faster inference and lower memory footprint, making it suitable for deployment in environments like Google Colab.
  * **Interactive UI:** Includes a [Gradio](https://gradio.app/) interface for real-time testing and interaction.

## Prerequisites

To run this project, you need the following libraries installed:

```bash
pip install streamlit transformers datasets pyngrok accelerate gradio
```

## Project Structure

  * **Data Preparation:** 5000 samples are selected from the Amazon dataset. Labels are mapped to specific assistant responses:
      * **Positive (Label 1):** "Thanks for your positive review\! We are happy you liked the product."
      * **Negative (Label 0):** "We are sorry for your experience. We will improve our service."
  * **Tokenization:** Implements a custom tokenization function that ensures `labels` are correctly mapped for causal language modeling.
  * **Training:** Configured for 2 epoch with a small batch size to prevent OOM (Out of Memory) errors.
  * **Deployment:** A Gradio-powered web interface allows users to input their own reviews and see the bot's response.

##  Model Details

  * **Base Model:** `distilgpt2`
  * **Max Length:** 128 tokens
  * **Batch Size:** 2
  * **Training Epochs:** 1
