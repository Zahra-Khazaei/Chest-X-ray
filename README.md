# Chest-X-ray

This project is one of my assignments related to https://www.coursera.org/ in AI for Medicine Specialization.
This Course includes three different courses entitled: AI for Medical Diagnosis, AI for Medical Prognosis and AI For Medical Treatment
Chest-X-ray is an assignemtn for the first course; ie AI for Medical Diagnosis


## Table of Contents

1. [Objective](#objective)
2. [Dataset](#dataset)
3. [Data Leakage](#data-leakage)
4. [Preprocessing](#preprocessing)
5. [Class Imbalance](#class-imbalance)
6. [Model](#model)
7. [Contact](#contact)


## Objective

* Explore medical image diagnosis and classify chest X-ray dataset by Deep Learning



## Dataset

The ChestXray8 [dataset](https://arxiv.org/abs/1705.02315)
consists of frontal-view images(108,948) of 32,717 patients.


* Each image have 14 different pathological conditions as its multiple text-mined labels.
* It leads to be used by doctors to diagnose 8 different diseases.
* The model will be predict pathologies by the world of 'positive' or 'negative'.

However, to make it simpler, I used a provided image subset (1000 images). 
You can download the provided image subset [here](https://drive.google.com/drive/folders/1k08jlnxKIpP3UImBiriX2Kz4hdUyxWzu?usp=share_link).

nih/train-small.csv: 875 images for training.
nih/valid-small.csv: 109 images for validation.
nih/test.csv: 420 images for testing.

You can download these CSV files [here](https://drive.google.com/drive/folders/19GLbu2KmzOZfYo_dXA7fhWxsXml4tJYr?usp=share_link).

This dataset has been annotated by consensus among four different radiologists for 5 of our 14 pathologies:

* Consolidation
* Edema
* Effusion
* Cardiomegaly
* Atelectasis

## Data Leakage

We should prevent data leakage. But, what is exactly data leakage?
When a patient has taken multiple X-ray images at different times, maybe some images will be repetetive between train, validation and test datasets. It is obvious that we want to have unique images in each these three datasets.
We'll use a function for checking this problem to make sure there are no patients in the test set that are also present in either the train or validation sets.


## Preprocessing

There is a class entitled ImageDataGenerator from the Keras framework.
It has many applications for example:
* You can do random horizontal flipping of images.
* You can normalize the values(the mean is 0 and STD is 1).
* You can convert your single channel images to three channel images.



## Class Imbalance

There is another problem that we can face it when we are using medical images. If we plot the frequency of each of the labels we will figure out number of some diseases are much more than others. For example, healthy people are more than sich people.
If we use a normal cross-entropy loss function with an unbalanced dataset our model will be uncentivized to prioritize the majority class.(i.e negative in our case). So it is better to change our loss formulation.



## Model 

It is used a pre-trained [DenseNet121](https://www.kaggle.com/datasets/pytorch/densenet121) model and then it is added two layers on top of it:
* A GlobalAveragePooling2D layer
* A Dense layer with sigmoid activation


## Contact

If you have any anything to tell, I will be glad to hear from you: my Email is Zahra1997khazaei@gmail.com
Also, I will be happy to visit my [website](https://el-ham.com/)