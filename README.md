# Capstone Project: Team KaBoBe
##### by [Margaux Borgmann](https://github.com/margauxbo), [Leon Becker](https://github.com/M4rl0wBuongustaio) & [Yvonne Kasche](https://github.com/princessivy) in cooperation with [snapADDY GmbH](https://www.snapaddy.com/de/index.html)

### important information: see [Interaction between SimpleTransformers (huggingface) and fastai](https://github.com/pds2122/capstone-project-kabobe/blob/main/supplementary_file/findings_during_project.md#interaction)

> Deep Learning does not shine. Our App does! :-P



#### Table of Contents
- [Introduction](#intro)
- [Overview of Files](#files)
- [Getting the Data to run the App](#dataset)

<a name="intro"></a>
## Introduction

`Goal`: Develop an app that classifies a company's landing page into one of 19 industries*.  
`Status`: DONE.

  
 \* *the 19 industries are: Automotive, Construction, Consumer Goods, Financial Services, Human Resources, Information Technology and Services, Insurance, Legal Services, Leisure Travel and Tourismn, Logistics and Supply Chain, Management Consulting, Marketing and Advertising, Mechanical or Industrial Engineering, Medical Practice, Real Estate, Recreational Facilities and Services, Renewables and Environment, Telecommunications, Wholesale.*
 
<a name="files"></a>
## Overview of Files
#### Files on the [landingpage](https://github.com/pds2122/capstone-project-kabobe) of the repository:
| File | Description |
| --- | --- |
| [gradio_app.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/gradio_app.ipynb) | final application with GUI |
| [preprocessing.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/preprocessing.ipynb) | the preprocessing that was used for preparing the train- and test-data as input for the training of the models |
| [preprocessing_methods.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/preprocessing_methods.ipynb) | isolated methods from [preprocessing.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/preprocessing.ipynb) for the import into [gradio_app.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/gradio_app.ipynb) for editing the url entered into the GUI to make the prediction |

#### Files in Folder ["models"](https://github.com/pds2122/capstone-project-kabobe/tree/main/models)
| File | Description |
| --- | --- |
| [model_logistic_regression.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/models/model_logistic_regression.ipynb) | Baseline Model: Logistic Regression |
| [model_ml_xgboost.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/models/model_ml_xgboost.ipynb) | Machine Learning Model: XGBoost |
| [model_dl_fastai.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/models/model_dl_fastai.ipynb) | Deep Learning Model: AWD_LSTM, fastai |
| [model_zero_shot.ipynb](https://github.com/pds2122/capstone-project-kabobe/blob/main/models/model_zero_shot.ipynb) | Deep Learning Model: Zero Shot bert-base-cased, huggingface |
| [folder "model_metrics"](https://github.com/pds2122/capstone-project-kabobe/tree/main/models/model_metrics) | shows the metrics for the models |

#### Files in Folder ["supplementary_file"](https://github.com/pds2122/capstone-project-kabobe/tree/main/supplementary_file)
| File | Description |
| --- | --- |
| [ideas_during_project.md](https://github.com/pds2122/capstone-project-kabobe/blob/main/supplementary_file/ideas_during_project.md) | ideas during the project, especially for the features |
| [findings_during_project.md](https://github.com/pds2122/capstone-project-kabobe/blob/main/supplementary_file/findings_during_project.md) | findings during the project, especially with respect to train- and test-data in the models |
| [Content-based and link-based methods for categorical webpage classiﬁcation.pdf](https://github.com/pds2122/capstone-project-kabobe/blob/main/supplementary_file/Content-based%20and%20link-based%20methods%20for%20categorical%20webpage%20classiﬁcation.pdf) | paper used for our approach |

<a name="dataset"></a>
## Getting the Data to run the App

This [link](https://drive.google.com/drive/folders/1qR-9z3uFmp5Nvsb_1QrR9lU8yNE8hi6l) mounts you to the data used in this project (provided von GoogleDrive).  
*[for using the data, just create a linkage to your personal drive and mount with gdrive]*  

#### Files in GoogleDrive-Folder ["archive"](https://drive.google.com/drive/folders/1Ck-zD0C9wl4BDKXqAYPlIcQrF-JZCNn-)
These files were created during the project and are irrelevant. They just save important intermediate steps.

#### Files in GoogleDrive-Folder ["data"](https://drive.google.com/drive/folders/15bLOMipTrOISMtqO1-iuYFdEienS7P-M)

| File | Description |
| --- | --- |
| folder [data_temp_steps](https://drive.google.com/drive/folders/1BMizbwxpZP8dVCZM8zoO8u6eTGnKfxdl) | data for intermediate steps. this data is now irrelevant |
| folder [language](https://drive.google.com/drive/folders/1iGSakmsnlUYkdyisAhEcrnlnlX4lcd1W) | a split of the train-dataset into english and german|
| folder [final](https://drive.google.com/drive/folders/1u-vHeAERFmj91UAU-t8toAWm3OtokUel) | the train- and test-dataset used to train all the models [just german language]|

#### Files in GoogleDrive-Folder ["models"](https://drive.google.com/drive/folders/16H3iaGO4CTFqyDa-SMcXsRKFT09qQmZM)
These folders contain the saved models that have been trained and validated on the data from [final](https://drive.google.com/drive/folders/1u-vHeAERFmj91UAU-t8toAWm3OtokUel). These models are the base for the prediction of the industry-label in the application.  
Link to the models-data:
- Baseline Model: [Logistic Regression](https://drive.google.com/drive/folders/1NPj0G5FZO_yC7V_mtDI5z-_vgtnRlZuM)
- Machine Learning Model: [XGBoost](https://drive.google.com/drive/folders/1yPXkgNjbLI5eo__1FirShdzYVxoEzCdI)
- Deep Learning Model: [AWD_LSTM, fastai](https://drive.google.com/drive/folders/1C1nhBBhhmSY3zRxUviN4BXIM8nSiWDMg)
- Deep Learning Model: [Zero Shot distilbert-base-german-cased, huggingface](https://drive.google.com/drive/folders/1Uzyj2UI9ZdC6KO3dMPIp1nVtprTLK0-J)

