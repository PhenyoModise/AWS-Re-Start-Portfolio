Training a Machine Learning Model
---

**Lab overview**

Explore the biomechanical vertebral column dataset, first split the dataset into three separate datasets for training, validation, and testing. I will then use this data to train a machine learning (MML) model by using the XGBoost algorithm.

---- 

**Objectives**
- Split data into training, validation and test datasets
- Train a XGBoost model in Amazon SageMaker

-----

_**Task 1: Accessing a notebook instance in Amazon SageMaker**_

In this task, I shall open my JupyterLab environment and switch to the notebook to complete the lab.
To open JupyterLab:
1. At the top of the AWS Management Console, in the search bar, search for and choose Amazon SageMaker AI.
 <img width="750" height="340" alt="image" src="https://github.com/user-attachments/assets/a666b7b1-908e-4246-83d2-62d01233276c" />
 
&nbsp;

2. From the navigation menu on the left, expand the **Applications and IDEs** section and choose **Notebooks** and then choose **Notebook instances** tab from lower pane.
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/bdc163be-377f-4805-8b9b-b2e90d270df0" />

&nbsp;

3. I searched for the notebook instance named **MyNotebook**. Open the JupyterLab notebook instance by going to the end of the row and choosing **Open JupyterLab**.
<img width="768" height="400" alt="image" src="https://github.com/user-attachments/assets/837d9d9c-b8f0-4d86-b530-9a72ca1d3864" />

-------
_**Task 2: Opening a notebook in your notebook instance**_

Opening the notebook for this lab:
1. In my JupyterLab environment, I navigated to the file browser in the left pane and located the 3_4-machinelearning.ipynb file.
<img width="740" height="353" alt="image" src="https://github.com/user-attachments/assets/752f1fa6-ee6d-4ddb-94a6-c37d0e4372ad" />

&nbsp;

2. I opened the _en_us/3_4-machinelearning.ipynb_ file by clicking it.
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/10b1db6a-5165-4c65-92d8-f54ca9349999" />

-------

_**Importing the data**_

By running the below cells, the data will be imported and ready for use:

**python**

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/b96bc15a-d183-4fed-93ba-0580d35272dd" />

----
_**Step 1: Exploring the data**_

use **shape** to examine the number of rows and columns.

<img width="480" height="138" alt="image" src="https://github.com/user-attachments/assets/efbd0cd7-90c5-4e0b-b426-a64c61ac6e85" />

&nbsp;

Columns:

<img width="740" height="180" alt="image" src="https://github.com/user-attachments/assets/aa655c57-00e7-4344-a597-f8ffc2a88374" />

------
_**Step 2: Preparing the data**_

For this section, I must split the data into three datasets.
An internet search will show many different ways to split datasets. Many code samples that you might find will split the dataset into the target and the features. Then, they will split each of those two datasets into three subsets, which results in a total of six datasets to track.
-	Moving the target column position
-	XGBoost requires the training data to be in a single file. The file must have the target value be the first column.
  <img width="700" height="340" alt="image" src="https://github.com/user-attachments/assets/4637e806-75da-478f-8c5a-ccf74dafe3ab" />

------
**Splitting the data**

I will start by splitting the dataset into two datasets. One dataset for training and split the other dataset again for use with validation and testing.

This is done by using  the _train_test_split_ function from the scikit-learn library.
<img width="740" height="58" alt="image" src="https://github.com/user-attachments/assets/3db2ca25-0bdc-4f22-b71b-514522b8dfc1" />

&nbsp;

split the _test_and_validate_ dataset into two equal parts.
<img width="740" height="34" alt="image" src="https://github.com/user-attachments/assets/f078f07b-faa0-4b98-97e7-b201292667fd" />

&nbsp;

Examine the three datasets.

<img width="382" height="255" alt="image" src="https://github.com/user-attachments/assets/30c5dd9c-97e3-41f6-bd95-1dee321ef6aa" />

&nbsp;

the distribution of the classes.

<img width="630" height="400" alt="image" src="https://github.com/user-attachments/assets/37e84d9d-5729-4956-87da-0e19b24a4243" />

------
**Uploading the data to Amazon S3**

XGboost will load the data for training from Amazon Simple Storage Service (Amazon S3). Thus,the need to write the data to a comma-separated values (CSV) file and then upload the file to Amazon S3.

I start by setting up some variables to the S3 bucket, then create a function to upload the CSV file to Amazon S3. 
<img width="740" height="330" alt="image" src="https://github.com/user-attachments/assets/0816480e-d9c8-4805-bb0d-699eaeb016f3" />

&nbsp;

Uploading the 3 datasets:

<img width="759" height="120" alt="image" src="https://github.com/user-attachments/assets/7c63c3c1-7b23-4258-a1e0-2bb8fb02f1a0" />

-----
_**Step 3: Training the model**_

Now that the data in Amazon S3, I  can train the model.

The first step is to get the XGBoost container URI.
<img width="740" height="156" alt="image" src="https://github.com/user-attachments/assets/0062d681-3e93-49d0-ab24-3de3ee670c52" />

set **hyperparameters** for the model
<img width="772" height="117" alt="image" src="https://github.com/user-attachments/assets/e7beb7a1-70fb-484e-9250-f4b76c938511" />

&nbsp;

<img width="740" height="256" alt="image" src="https://github.com/user-attachments/assets/7f175cf0-e4da-4a04-a2dc-9eaccdc926c4" />

&nbsp;

The estimator needs channels to feed data into the model. For training, the **train_channel** and **validate_channel** will be used.
<img width="740" height="280" alt="image" src="https://github.com/user-attachments/assets/9b995fb4-6f07-426f-a949-d106f8102b9b" />

&nbsp;

Running **fit** will train the model.

<img width="740" height="260" alt="image" src="https://github.com/user-attachments/assets/0160b814-13bd-4782-824d-7834f9cbaa63" />



