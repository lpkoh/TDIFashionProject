# The Data Incubator
## Problem Statement:
Fashion inspiration today is found on social media sites like Instagram and Pinterest, but shopping is done on websites like Amazon. The transition from inspiration to shopping is often difficult, as after finding a piece of clothing, it is often difficult to locate/search for clothing of a similar nature to that. The idea is to build a feature extractor that can take in diverse input, whereby input from social media (posts, hashtags, images) can be transformed into features which then can be used in a recommendation system to recommend clothes.

This project focuses on building a text and image extractor that can work on social media posts.

## 1st Asset: Fashion images: Deepfashion, Instagram
### DeepFashion
To train an image to label and fashion images properly, we will use the DeepFashion data, which has over DeepFashion contains over 800,000 diverse fashion images ranging from well-posed shop images to unconstrained consumer photos. As we eventually plan to label fashion images on social media, the mix of posed shop images and unconstrained consumer photos is a good dataset to train on. Furthermore, we eventually want to test our feature extractor on social media posts, we will scrape some of these posts. Deepfashion dataset is extremely comprehensive, having a category and attribute prediction benchmark, landmark detection benchmark, etc.
![GitHub Logo](/images/attributes.jpg)
![GitHub Logo](/images/landmarks.jpg)

### Instagram

In addition, I also got an instagram scraper to run. This is the installation code:
```python
$ pip install instagram-scraper
```
To scrape, run:
```python
$ instagram-scraper <username> -u <your username> -p <your password>             
```
Providing username and password is optional, if not supplied the scraper runs as a guest.

To scrape a hashtag for media:
```python
$ instagram-scraper <hashtag without #> --tag
```

By running instagram scrapper on top fashion influencer Zoella, we get:
![GitHub Logo](/images/91263927_120041452958279_8151565705070408575_n.jpg)
![GitHub Logo](/images/91693460_2724881547623151_4953905862608554348_n.jpg)

By running instagram scrapper on hashtag ootd (outfit of the day), we get:
![GitHub Logo](/images/89830452_138197107721093_3195444993594625119_n.jpg)
![GitHub Logo](/images/19933281_250367215466764_3000932124032237568_a.jpg)

## 2nd Asset: Word embeddings
We also need a way to extract features from textual data. An example of how this can be done is using a pretrained word vector model, that we could possibly tune, to extract word vectors. We could also fine tune other state of the art embedding models such as BERT, with fine tuning on fashion dataset.

We demonstrate this is feasible using a simple word2Vec model, which we use on Amazon fashion product titles. Attached is visualization of word embeddings for words found in titles of Amazon products under "Clothing, Shoes and Jewelry", after PCA to 2 dimensions.
It is titled "wordEmbeddingsGenerated.png"
Requisite data is found under meta data of "Clothing, Shoes and Jewelry": http://deepyeti.ucsd.edu/jianmo/amazon/index.html

![GitHub Logo](/images/wordEmbeddingsGenerated.png)

The word embeddings here are imperfect, but they do show some understanding of the context of meaning of the words. For example, leather is closely related to waterproof. However, most words are still quite clustered, and indicate much area for improvement which also offers an opportunity.  A future direction for word similarity models could be similarities trained on specifically fashion datasets, as well as extending similarity to phrases and product descriptions, and lastly tuning state of the art models in textual similarity for this task.
