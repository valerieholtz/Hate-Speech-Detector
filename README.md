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

A research approach on German Hate Speech Detection is described in the following paper: https://arxiv.org/pdf/1701.08118.pdf. The last years have seen an increase of Hate Speech in Social Media and a need for automated detection and filtering of such. Although there is no universally agreed upon definition what Hate Speech is, in the following project it can be seen as „abusive speech targeting specific group characteristics. such as ethnic origin, religion, gender or sexual orientation.“ (Ross et al., 2017, p. 2) A general problem in this field is the complexity of the topic. Detecting Hate Speech is more than just detecting swear words. What is considered Hate Speech can be personal interpretation, depends on someones background and personal sensibilities. As such, classifying Hate Speech is not a straight forward task. An issue researchers  encounter when labelling the data. Another problem one encounters when trying to detect Hate Speech in languages other than English is the  lack of annotated datasets and puplicly available work done. A problem that is also really prevent for the German language. ibid., p.2f.)

## Data

Due to the lack of a bigger German Hate Speech text corpus, one workaround was the combination of different, smaller annotated datasets that were made publicly available online, mostly from research projects on the topic. Through this I ended up with a German Hate Speech corpus of mostly tweets and posts from Facebook from the years 2016-2020. As expected with such a topic, the dataset was imbalanced with roughly 4 thousand cases of Hate Speech and 15 thousand cases of not Hate Speech labeled data.

<img src="https://user-images.githubusercontent.com/79086000/145720998-9481dc37-4a45-4bbc-ad7e-d90f6142c79d.png" width="300">

One problem I encountered in combining the different datasets was in the labelling of the classes.
As Ross et all. (2017) stated, there is no clear definition on Hate Speech so the labeling varied from dataset to dataset, some working with a scale, some with binary classification etc.. I tried my best to smooth the labelling as much as possible to make a consistently labeled dataset with binary classification.

See the end of file for citation.

## Visual Analysis

Pre analysing the data before the modelling gave interesting insights, that only confirmed the research prior to the modelling. It was interesting to confirm a few pre-conceptions, such as the fact that Hate Speech targets specific group characteristics, such as ethnic origin and religion.

*WordCLoud - Hate Speech*

<img src="https://user-images.githubusercontent.com/79086000/145720382-6de0654e-acd5-445e-87fc-d6500f4da49f.png" width="600">

A look the most frequent used words in each sub-set - Hate Speech and other -  showed an overview of the content of each. While the topics of discussion were similar, ‚other‘ had a more balanced word choice, ‚Hate Speech‘ focused a lot on vulgar or biased language.

*WordCLoud - neutral*

<img src="https://user-images.githubusercontent.com/79086000/145720397-6b3ec952-421c-4b00-869f-b92aada3409d.png" width="600">


## NLP Model overview

Bert Model

My main goal in the data modeling phase was to compare different pre trained models and find the best for the task. A good solution to do this, especially in languages other than English is the Transformers library by HuggingFace. This gives a wide range of transformer-based pre-trained models in different languages. Exactly  I used the Simple Transformers library, which is built on top of the transformers library
The notebooks containing the models involves fine-tuning a Bert model. Due to the imbalanced dataset, the most important Hyperparameter to tune was the weight parameter. 4 models were fine tuned and tested for performance on the dataset. 
The model „deepset/bert-base-german-cased-sentiment-Germeval17" gave the best results with the following hyperparameters.

![image](https://user-images.githubusercontent.com/79086000/145720480-d6ca9ec5-298f-4b4c-8f4d-04c2ac8a18f6.png)

Especially taking into account the f1 score as a a good metric for a heavily imbalanced dataset and the model’s handling of the positive Hate Speech examples, seen in the AUPRC score and the confusion matrix.

*Results:*

<img src="https://user-images.githubusercontent.com/79086000/145720505-8ff5e865-7550-4d2d-b628-349a0b0fb2a5.png" width="350">

*Confusion Matrix:*

![image](https://user-images.githubusercontent.com/79086000/145720517-9b52aa70-0d1c-49b5-be8e-4bdb33e4b5d7.png)

## Evaluation

As it was the goal to detect complex cases of Hate Speech, for the model evaluation the performance on fitting real life examples was taking into account. As expected with the f1 and AUPRC score, „deepset/bert-base-german-cased-sentiment-Germeval17“ performed best on examples as the following: 

![image](https://user-images.githubusercontent.com/79086000/145720530-0fd4bb02-03b8-4dd2-a8cf-15cf946ef0a5.png)

## Sources

I would like to thank everyone involved in the development of the datasets, which were incredibly well done. This project would not have been possible without a nicely collected and cleaned-up data.

The datasets can be found here: 

https://github.com/UCSM-DUE/IWG_hatespeech_public
Ross, B., Rist, M., Carbonell, G., Cabrera, B., Kurowsky, N. and Wojatzki, M., 2017. Measuring the Reliability of Hate SpeechAnnotations: The Case of the European Refugee Crisis. ArXiv,.


http://ub-web.de/research/
Bretschneider, U. and Peters, R., 2017. Detecting Offensive Statements towards Foreigners in Social Media. In: Proceedings of the 50thHawaii International Conference on System Sciences.

https://github.com/uds-lsv/GermEval-2018-Data
Wiegand, M., Siegel, M. and Ruppenhofer, J., 2018. Overview of the GermEval 2018 Shared Task on the Identification of OffensiveLanguage. In: Proceedings of GermEval 2018, 14th Conference on Natural Language Processing (KONVENS 2018). Vienna, Austria: Research Gate.

https://hasocfire.github.io/hasoc/2019/dataset.html
Mandl, T., Modha, S., Majumder, P., Patel, D., Dave, M., Mandlia, C. and Patel, A., 2019. Overview of the HASOC track at FIRE 2019.In: Proceedings of the 11th Forum for Information Retrieval Evaluation,.
