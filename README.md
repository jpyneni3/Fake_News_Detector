# Fake_News_Detector
CS 7650/4650 Course Project


| Directory               | Description                                                              |
|-------------------------|--------------------------------------------------------------------------|
| Augmentation Data | Cleaned data generated through data augmentation |
| Cleaned Data | Aggressively cleaned original data  |
| Experiments | Documentation of each experiment |
| Notebooks | Notebooks used for data aggregation and augmentation |
| Uncleaned Data | original data without cleaning |

## 1) Data Collection
### Requirements (only for Scrapper tool)
Python Libraries:
```
pandas
feedparser
json
newspaper
csv
urllib.parse
```

| File | Location | Source|
|--------------|--------------------------|----------------------|
| LIAR Dataset | Uncleaned Data/liar_dataset | https://www.cs.ucsb.edu/ ̃william/ data/liar_dataset.zip |
| Kaggle Fake News | Uncleaned Data/Human_Fake_News.csv | https://www.kaggle.com/mrisdal/fake-news |
| Kaggle Real News | Cleaned Data/Kaggle3_Real.csv | https://www.kaggle.com/snapcrack/all-the-news |
| Kaggle Mixed News | Uncleaned Data/fake-news | https://www.kaggle.com/c/fake-news/data |
| Web scraped Real News | Uncleaned Data/Real_News.csv | Scraped using tool|

Most of the the datasets were downloaded directly from the sources. The Kaggle Real News dataset was too large to put on Github before cleaning so it was directly added to cleaned data after pre-processing for necessary articles.

The web scraped real news was obtained by running the scrapper tool (Notebooks/Scrapper.ipynb). The tool reads from specified RSS feeds (Notebooks/News_RSS.json) to extract the latest news. It was ran several times over the course of five days to obtain the current set of data.


## 2) Data Pre-Processing/Cleaning
### Requirements
Python Libraries:
```
nltk
pandas
numpy
```

There are three times where the data needs to be cleaned:
1) Unclean Data  --> Cleaned Data :
    Agressive cleaning of collected data to run base models on
2) Unclean Data --> Semi Clean Data:
    Semi cleaning of collected data to prepare for data augmentation
3) Augmentation Data --> Clean Augmentation Data:
    Agressive cleaning of augmented data to run models on

In each step, the data cleaning notebook is at Notebooks/DataPreprocessing/DataCleaning.ipynb. In the notebook, you can specify where to pull the data from and where to put after cleaning. For either of the aggressive cleanings, use the clean_column method and for the middle process, use the semi_clean_column method. The notebook right now contains the code to agressively clean the Synonym Replacement Augmentation Data for readying for models.

## 3) Data Augmentation
### Requirements:
```
pandas
nltk
torch
fastBPE
sacremoses
```
| Augmentation Technique   | Location  | Steps |
|-------------------------|---------------------| ------------------------------------------|
|Synonym Replacement| Notebooks/DataAugmentation/Synonym Replacement.ipynb | Run the notebook and it will automatically collect the semi clean data and run Synonym Replacement. Takes about 5 minutes.|
|Backtranslation | Notebooks/DatAugmentation/Backtranslation.ipynb | Highly recommend to run on Google Colab with GPU Enabled. Copy the semi cleaned data into the "contents" and give access to your google drive account, from where you can take the backtranslation data. Takes about 26 hours with GPU.|

Data in the Augmentation Data/semi cleaned is the data upon which to run data augmentation. The outputs of those are placed in the parent directory Augmentation Data with a \_SR or \_BT appended to the file name to denote output of Synonym Replacement or Backtranslation, respectively. Furthermore, this augmented data is pulled from the Augmentation Data for aggressive cleaning (3rd cleaning step above) and placed back in the same directory with a \_clean appended to the file name.
Examples:  
a) Augementation Data/semi cleaned/LIAR.csv --> LIAR dataset semi cleaned to run Data Augementation on  
b) Augementation Data/LIAR_SR.csv --> Output of running Synonym Replacement on semi cleaned LIAR dataset  
c) Augementation Data/LIAR_SR_clean.csv --> Aggressively cleaned Synonym Replacement output from LIAR dataset
