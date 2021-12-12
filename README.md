# Hate-Speech-Detector

## Description

This project develops a model for binary classification on German language Hate Speech sentences in Social Media. To accomplish this I am using the Bert (Bidirectional Encoder Representations from Transformers) language model. 

Components of the project:
- A notebook with data preparation and EDA on the dataset found in Data_Wrangling.ipynb and EDA.ipynb.
- A notebook with the most promising Bert modeling approach found in model_germeval17.ipynb.
- Notebooks with more Bert modeling approaches found in model_selection.


## Goal

The goal of this project is to train a model that detects complex cases of Hate Speech, meaning cases that do not necessarily contain vulgar language, but are nonetheless extremely aggressive against individuals or a group of people.

## Key words

Python

NLP

BERT

SimpleTransformers

HuggingFace

Text Classification

GoogleCollab

## Background

A research approach on German Hate Speech Detection is described in the following paper: https://arxiv.org/pdf/1701.08118.pdf. The last years have seen an increase of Hate Speech in Social Media and a need for automated detection and filtering of such.Although there is no universally agreed upon definition what Hate Speech is, in the following project it can be seen as „abusive speech targeting specific group characteristics. such as ethnic origin, religion, gender or sexual orientation.“ (Ross et al., 2017, p. 2) A general problem in this field is the complexity of the topic. Detecting Hate Speech is more than just detecting swear words. What is considered Hate Speech can be personal interpretation, depends on someones background and personal sensibilities. As such, classifying Hate Speech is not a straight forward task. An issue researchers  encounter when labelling the data.Another problem one encounters when trying to detect Hate Speech in languages other than English is the  lack of annotated datasets and puplicly available work done. A problem that is also really prevent for the German language. ibid., p.2f.)

## Data

Due to the lack of a bigger German Hate Speech text corpus, one workaround was the combination of different, smaller annotated datasets that were made publicly available online, mostly from research projects on the topic. Through this I ended up with a German Hate Speech corpus of mostly tweets and posts from Facebook from the years 2016-2020. As expected with such a topic, the dataset was imbalanced with roughly 4 thousand cases of Hate Speech and 15 thousand cases of not Hate Speech labeled data.
One problem I encountered in combining the different datasets was in the labelling of the classes.
As Ross et all. (2017) stated, there is no clear definition on Hate Speech so the labeling varied from dataset to dataset, some working with a scale, some with binary classification etc.. I tried my best to smooth the labelling as much as possible to make a consistently labeled dataset with binary classification.
See the end of file for citation.
