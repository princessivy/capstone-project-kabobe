### Table of Contents
Here, you can read about important decisions and noteworthy findings in our project process.  
- [Features](#features1)
  -  [Features from html](#features2)
  -  [Additional Features](#features3)
  -  [Regarding the lang_code](#features4)
  -  [Regarding the sentiment_analysis](#features5)
- [Models](#models)
  -  [Interaction between SimpleTransformers (huggingface) and fastai](#interaction)
  -  [BERT - Zero shot (huggingface)](#bert)
- [Data](#data)
  -  [Train- and test-data scores](#scores)
  -  [Data loader and "data saver"](#loader_saver)

<a name="features1"></a>
## Features
<a name="features2"></a>
### Features from html
In [preprocessing.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/preprocessing.ipynb), we first looked at the occurence of all tags from the htmls. The occurence was used as a base to decide, which features are the most important:
  - img_alt
  - title
  - h1
  - h2
  - h3
  - strong
  - bold
  - figcaption

After the contents of the features were extracted for all rows in the datasaset, they were checked for completeness. This resulted in following (based on test-dataset):
| Feature | % empty |
| --- | --- |
| img_alt | 11.35% |
| title | 0.23% |
| h1 | 29.11% |
| h2 | 15.89% |
| h3 | 26.73% |
| strong | 42.22% |
| bold | 99.99% |
| figcaption | 94.96% |

We decided not to pay further attention to the features which are empty in more than 50%. So, *bold* and *figcaption* are no longer independent features.  

<a name="features3"></a>
### Additional Features
We also extend our features with *concatinated*, *sentiment_analysis* and *lang_code*.  
The *concatinated*-Feature merges all html-features (including *bold* and *figcaption* - these were only excluded as independent features).  
With *lang_code* we determine the language of the html-page. Therefore we use the libaray `langdetect` on the convertHTML-Body, which we returne with the library `bs4`. That's how we filtered the data by language. You can find results in [GoogleDrive](https://drive.google.com/drive/folders/1iGSakmsnlUYkdyisAhEcrnlnlX4lcd1W).  
The *sentiment_analysis* is based on *concatinated* and comes from the library `textblob`.

<a name="features4"></a>
### Regarding the lang_code
As we already mentioned, at the moment we focus on developing models for German websites. Overall there are 16809 in the train- and 8396 in the test-dataset. In [preprocessing.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/preprocessing.ipynb), we nevertheless developed a good start to preprocess english html-data. The code therefore is marked out. In further development this idea can be used to differentiate between languages (instead of language detector) and use a model that was trained with English data.


<a name="features5"></a>
### Regarding the sentiment_analysis
The *sentiment_analysis*, which results from *concatinated*, improves the models - even if only marginally.  
If you take a look at the mean-value in respect of the industry-labels, you will see that they are very close to each other, as the following table shows (based on test-dataset):  

| Industry-Label | Mean |
| --- | --- |
| Automotive | 0.143573 |
| Construction | 0.118420 |
| Consumer Goods | 0.142469 |
| Financial Services | 0.131865 |
| Human Resources | 0.135658 |
| Information Technology and Services | 0.130944 |
| Insurance | 0.135061 |
| Legal Service | 0.106525 |
| Leisure, Travel and Tourism | 0.218068 |
| Logistics and Supply Chain | 0.128015 |
| Management Consulting | 0.121037 |
| Marketing and Advertising | 0.134258 |
| Mechanical or Industrial Engineering | 0.112010 |
| Medical Practice | 0.140171 |
| Real Estate | 0.138664 |
| Recreational Facilities and Services | 0.162923 |
| Renewables and Environment | 0.142895 |
| Telecommunications | 0.128065 |
| Wholesale | 0.145271 |

The label *Leisure, Travel and Tourism* is the most positive with > 0.21. The label *Legal Service* is the least positive with <0.11.



<a name="models"></a>
## Models

<a name="interaction"></a>
### Interaction between SimpleTransformers (huggingface) and fastai
During the integration process in the App, we noticed that only one of the two libraries (SimpleTransformers (huggingface) OR fastai) can be installed and executed without problems. Importing and executing both means that one (in most cases huggingface) does not work. We have tried to solve this problem with an if-else (version variable), so that you have to select in advance, which library you want to proceed with.  

<a name="bert"></a>
### BERT - Zero shot (huggingface)
In the frist approach to implement a zero shot model we followed the tutorial in lecture 09. This worked out well in the first run. The model was saved on the drive. But, the accuracy was very low, so that we decided to run a German specific distilBERT zero shot model. This works better and is thus integrated in the app. Nonetheless, the code for the inital model is still submitted for completeness. 

The finding we made when executing the model in a second/third/forth run is that is automatically requests the wandb API. As we don't have an account at "Weights & Biases" and the data was requested to be kept private, we didn't want to create the connection. This causes the bert-model to stop predicting even if trained. The setting "report_to=None" didn't make a difference. Disabling wandb causes problems in training.




<a name="data"></a>
## Data
<a name="scores"></a>
### Train- and test-data scores
As recommened, we focussed on developing an initial model (logistic regression as our baseline-model) quickly and then improving it. In order to do so, we first preprocessed the training dataset and worked with than on our models. We used a regular train-test-split and StratifiedKFold. Here, we achieved an accuracy score up to 0.78.

Over the project we also preprocessed the test datatset using the same methods as on the train data. When integrating the test data to the models, the scores went down in the logistic regression and xgboost. The accurarcy of prediction was about 10% worse than before.

*How come?*
A possible explaination is that the distribution of the test-data isn't the same as the one of the train-data. 

Other tests: When concatenating test- and train-data to one dataset and then using StratifiedKFold with cross-validation in the logistic regression, the scores went up again, to an accuracy of about 0.74.


<a name="loader_saver"></a>
### Data loader and "data saver"
Due to a very large train data set, it was hard to work with all the available data in the GoogleColab environment. With the given data loader, the ndjson was read line per line so that the runtime didn't crash. To save the data we built a corresponding "data saver" that loaded the data back to a ndjson file. This also happened row based. The method enabled us to keep working on Colab and save our preprocessed data correctly without crashing the runtime.  
We are actually very proud of this, as it meant we do not have to get a pro-account on GoogleColab. 
