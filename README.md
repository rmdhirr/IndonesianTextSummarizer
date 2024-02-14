# Bert2GPT Indonesian Text Summarizer
This repository hosts a sequence-to-sequence model that employs BERT for encoding and GPT for decoding, crafted specifically for the task of text summarization. The model is optimized for the Indonesian language, having been fine-tuned on the 'id_liputan6' dataset. This dataset is comprised of text summarization data derived from Liputan6, a prominent Indonesian news website. The ultimate goal of this project is to deliver succinct and accurate summaries of Indonesian news articles.

---

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Results](#results)
- [Room For Improvement](#room-for-improvement)
- [References](#references)
- [Attachment](#attachment)

---
# Introduction

The Bert2GPT Indonesian Text Summarizer is a sequence-to-sequence model that combines the encoding capabilities of BERT with the decoding prowess of GPT, specifically designed for the task of text summarization within the Indonesian context. This model addresses the growing need for efficient information processing in the face of increasing digital content, particularly in news media.

Indonesia's diverse linguistic landscape and the proliferation of digital news platforms necessitate advanced tools for content comprehension. The Bert2GPT Indonesian Text Summarizer caters to this need by providing a mechanism to distill lengthy news articles into their essential summaries, thus aiding in rapid information assimilation.

Housed in this repository is a model meticulously fine-tuned on the 'id_liputan6' dataset, which comprises text summarization pairs sourced from Liputan6, one of Indonesia's prominent news websites. This choice of dataset ensures that the model is well-adapted to the Indonesian language's syntactic and semantic nuances, as well as the stylistic characteristics typical of local news reporting.

The primary objective of the Bert2GPT Indonesian Text Summarizer is to enhance the accessibility of news content by generating concise and coherent summaries. This endeavor aligns with the broader goal of leveraging AI to bridge the gap between vast information streams and the end-user's need for quick and reliable insights. Through this project, I aim to contribute to the domain of natural language processing by offering a tool that not only streamlines content consumption but also fosters a better-informed and engaged audience in the Indonesian digital ecosystem.

---
# Dataset

## Finetuning Corpus

For the Bert2GPT Indonesian Text Summarizer, the canonical subset of the id_liputan6 dataset, accessible via the [Hugging Face](https://huggingface.co/datasets/id_liputan6) platform, serves as the foundation for the model's finetuning. This dataset, specifically curated from Liputan6 — a prominent Indonesian news website — offers a rich collection of text summarization pairs that are pivotal for training models in the Indonesian language context.

The id_liputan6 dataset is structured into two distinct parts:

- Xtreme Set: Designed for more challenging summarization scenarios, the Xtreme set features a diverse range of text lengths and complexities. It is intended to push the boundaries of summarization models in terms of understanding and generating concise summaries from more intricate articles.

- Canonical Set: This portion of the dataset provides a standard benchmark for summarization tasks, with a larger set of examples for training, development, and testing. It is characterized by its balanced representation of various news categories, making it ideal for general summarization models.

The canonical set is characterized by its comprehensive coverage, including a balanced mix of topics and writing styles reflective of mainstream Indonesian news reporting. This aspect of the dataset ensures that the finetuning process incorporates a wide array of linguistic nuances and information structures typical of Indonesian news articles.

By utilizing the canonical subset, the Bert2GPT model is exposed to a vast and varied corpus during finetuning, enabling it to learn and adapt to the complexities of summarizing news content accurately. The choice of this subset is strategic, aiming to equip the model with the ability to generate summaries that are not only concise and coherent but also faithful to the original articles in terms of content and tone.

The decision to employ the canonical subset underscores the project's commitment to creating a summarization tool that is highly attuned to the specifics of the Indonesian news landscape, ensuring relevance and applicability across a broad spectrum of news content.

---

# Methodology

## Exploratory Data Analysis

The Exploratory Data Analysis (EDA) section provides comprehensive insights into the dataset used for training the Bert2GPT Indonesian Text Summarizer. This section outlines various analytical steps taken to understand the dataset's characteristics, which inform the model's development and fine-tuning process.

### 1. Distribution of Article Lengths
This step involves analyzing the lengths of the articles in the dataset to understand the distribution and identify any potential outliers or biases. The analysis is visualized using a histogram, offering a clear view of how article lengths vary.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/115a8328-2a5a-4f4e-b887-d31aac9b4eb0)

### 2. Distribution of Summary Lengths
Similar to the analysis of article lengths, this step focuses on the lengths of the summaries. Understanding the summary lengths is crucial for modeling the summarization process, ensuring that the generated summaries are concise yet informative.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/67fb604e-5576-45c5-9b30-f820f0068aa3)

### 3. Most Frequent Terms in Articles
Identifying the most frequent terms in the articles helps in understanding the common themes and topics covered. This analysis is visualized through a bar plot, showcasing the top terms and their frequencies.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/50ab42d3-ce77-4435-aa35-6cee216cbb83)

### 4. Most Frequent Terms in Summaries
This step parallels the analysis of articles, focusing instead on the summaries. By identifying the most frequent terms in summaries, insights into the core information retained in the summarized content are gained.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/dff1ff2f-9b49-4857-b37e-702f79e087f3)

### 5. Scatter Plot for Article vs. Summary Length
A scatter plot comparing the lengths of articles and their corresponding summaries provides a visual representation of the summarization process, highlighting the compression ratio and the relationship between the original articles and the summaries.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/c71a9c10-00dc-43e0-b28b-dfb2099c903e)

### 6. Box Plot for Distribution of Text Lengths
A box plot offers a comparative view of the distribution of text lengths between articles and summaries. This visualization helps in understanding the variance and central tendency of lengths.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/2b87f8c3-a937-449c-b1d0-1f8f6396ccc9)

### 7. Plotting Bi-grams in Articles
Analyzing bi-grams (pairs of consecutive words) in articles reveals common phrase patterns, providing further insights into the linguistic characteristics of the dataset.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/a8ebc195-7e72-4ba0-ad32-ad9a899913ac)

### 8. Plotting Bi-grams in Summaries
This analysis extends the bi-gram analysis to summaries, helping to understand the phrase patterns prevalent in summarized content.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/07321033-14a3-4980-a855-d5dbfa3a032f)

### 9. Plotting Tri-grams in Articles
Tri-gram analysis in articles uncovers frequent three-word sequences, offering deeper insights into the contextual relationships within the text.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/0fc1dcb3-1525-436d-8595-b14837072b91)

### 10. Plotting Tri-grams in Summaries
Similar to articles, tri-gram analysis in summaries helps identify common three-word phrases, crucial for understanding the summarization style and content focus.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/3b7f3877-9d3c-435d-816f-43a99890c4c5)

### 11. Sentiment Analysis for Articles
Sentiment analysis of articles provides an overview of the emotional tone and sentiment polarity within the original content, essential for ensuring that the summaries accurately reflect the articles' intended sentiments.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/73e3a8f4-728a-46bd-891d-a431b4a5d16a)

### 12. Sentiment Analysis for Summaries
Extending sentiment analysis to summaries ensures that the emotional tone and sentiment polarity are preserved in the summarized content, maintaining the integrity of the original articles.

![image](https://github.com/aridofflimits/IndonesianTextSummarizer/assets/147245715/890ceacc-828d-4867-a1a8-34b33d9eb585)

### 13. Top Words in Topics
Topic modeling, such as Latent Dirichlet Allocation (LDA), applied to the articles, helps identify the major themes and topics present in the dataset. This analysis is crucial for ensuring the model is well-tuned to the content diversity.

```
Topic 1:
yang dan ini dari itu dengan untuk aceh dalam ke
Topic 2:
yang dan dengan dari untuk itu ini tidak ke akan
Topic 3:
yang dan ini warga dari untuk itu com liputan6 dengan
Topic 4:
yang dan itu ini jakarta dalam akan untuk dengan dari
Topic 5:
yang dan ini itu polisi dengan dari tak jakarta mereka
```
Each step in the EDA process contributes to a holistic understanding of the dataset, guiding the development and fine-tuning of the Bert2GPT Indonesian Text Summarizer to achieve optimal performance.

---

## Preprocessing

# Usage
Google Colab: [Bert2GPT](https://colab.research.google.com/drive/1x1l6m5rKQGUszmX3CkqHf9tpvKvMkpzB#scrollTo=gCEldMjP1FnD)
