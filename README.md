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

| File | Location | Source|
|--------------|--------------------------|----------------------|
| LIAR Dataset | Uncleaned Data/liar_dataset | https://www.cs.ucsb.edu/ ̃william/ data/liar_dataset.zip |
| Kaggle Fake News | Uncleaned Data/Human_Fake_News.csv | https://www.kaggle.com/mrisdal/fake-news |
| Kaggle Real News | Cleaned Data/Kaggle3_Real.csv | https://www.kaggle.com/snapcrack/all-the-news |
| Kaggle Mixed News | Uncleaned Data/fake-news | https://www.kaggle.com/c/fake-news/data |
| Web scraped Real News | Uncleaned Data/Real_News.csv | Scraped using tool|

Most of the the datasets were downloaded directly from the sources. The Kaggle Real News dataset was too large to put on Github before cleaning so it was directly added to cleaned data after pre-processing for necessary articles.

The web scraped real news was obtained by running the scrapper tool (Notebooks/Scrapper.ipynb). The tool reads from specified RSS feeds (Notebooks/News_RSS.json) to extract the latest news. It was ran several times over the course of five days to obtain the current set of data. 
