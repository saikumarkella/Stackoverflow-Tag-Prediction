# Stackoverflow-Tag-Prediction
The task is to predict the tags (a.k.a. keywords, topics, summaries), given only the question text and its title. The dataset contains content from disparate stack exchange sites, containing a mix of both technical and non-technical questions.

**Data Discription :**
Data was taken from the kaagle Facebook recuitment -III Keyword Extraction (StackOverflow Tag Prediction)

source : https://www.kaggle.com/c/facebook-recruiting-iii-keyword-extraction/data

**Data Overview**
<br>
All of the data is in 2 files: Train and Test.<br />
<pre>
<b>Train.csv</b> contains 4 columns: Id,Title,Body,Tags.<br />
<b>Test.csv</b> contains the same columns but without the Tags, which you are to predict.<br />
<b>Size of Train.csv</b> - 6.75GB<br />
<b>Size of Test.csv</b> - 2GB<br />
<b>Number of rows in Train.csv</b> = 6034195<br />
</pre>
The questions are randomized and contains a mix of verbose text sites as well as sites related to math and programming. The number of questions from each site may vary, and no filtering has been performed on the questions (such as closed questions).<br />
<br />

__Data Field Explaination__

Dataset contains 6,034,195 rows. The columns in the table are:<br />
<pre>
<b>Id</b> - Unique identifier for each question<br />
<b>Title</b> - The question's title<br />
<b>Body</b> - The body of the question<br />
<b>Tags</b> - The tags associated with the question in a space-seperated format (all lowercase, should not contain tabs '\t' or ampersands '&')<br />
</pre>

<br />


__PreProcessing__
- Body Contains Code sigments,Description,html tags
            
                Removed html tags and get rid of code sgments(assuming the code sniffet will varies much.), removed puncutations.
 - Title was in palin text so i removed some punctuations by using regular expressions.
 
__Observations__
- c#,c++,Jave Javascript ,jQuery are some of the Most Frequent Tags For the stackoverflow questions. (Mostly Frequent Tags are Programming language).
- Training with this huge amount dataset consumes large amount ram and takes lot of time to consume.

__Criteria__
- Due to have limations of ram . I used 0.5 million data points and restricted to use top 500 frequent labels for training and Validation.

Used Some MetaFeatures .
- These features are defined from the before Preprocessing and AfterPreprocessing the Dataset
- It helps to Increase accuracy slightly.

__Results For Mulitilabel Classification__


**Traning**
|Model|Accuracy_score|micro F1score|
|---|---|---|
|OneVsRest Classifier (hinge loss)|0.31153|0.5869313236695025|

-**Validation**
|Model|Accuracy_score|micro F1score|
|---|---|---|
|OneVSrest Classifer (log loss)|0.23079|0.46743106281454144|
|OneVsRest Classifier (hinge loss)|0.23316|0.4903430626194564|
|OneVsRest Classifier (modified_huber loss)|0.17696|0.42361195179662137|
 
