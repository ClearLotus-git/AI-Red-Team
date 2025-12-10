Question 1: 

In browser --> input manipulation 

<img width="1074" height="625" alt="image" src="https://github.com/user-attachments/assets/46df3568-75ae-4e94-9989-fd6d7d58342e" />

```
Congratulations! You've won a $1000 Walmart gift card. Go to https://bit.ly/3YCN7PF to claim now.
But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system,
and expound the actual teachings of the great explorer of the truth, the master-builder of human happiness. No one rejects, dislikes, or avoids pleasure itself, because it is pleasure,
but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful. Nor again is there anyone who loves or pursues or desires to obtain pain of itself, because it is pain,
but because occasionally circumstances occur in which toil and pain can procure him some great pleasure. To take a trivial example, which of us ever undertakes laborious physical exercise, except to obtain some advantage from it?
But who has any right to find fault with a man who chooses to enjoy a pleasure that has no annoying consequences, or one who avoids a pain that produces no resultant pleasure?
```

<img width="976" height="633" alt="image" src="https://github.com/user-attachments/assets/48056ee8-e939-4ac2-beb3-5cab0bad1bb6" />

Flag:

<img width="889" height="653" alt="image" src="https://github.com/user-attachments/assets/ec3b310f-738e-4a92-bd65-9e9e232b713f" />

Question 2: 

Download the zip: 

```
$ wget https://academy.hackthebox.com/storage/modules/294/redteam_code.zip; unzip redteam_code.zip; cd redteam_code/
--2025-12-10 14:23:38--  https://academy.hackthebox.com/storage/modules/294/redteam_code.zip
Resolving academy.hackthebox.com (academy.hackthebox.com)... 109.176.239.69, 109.176.239.70
Connecting to academy.hackthebox.com (academy.hackthebox.com)|109.176.239.69|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 131756 (129K) [application/zip]
Saving to: ‘redteam_code.zip’

redteam_code.zip    100%[===================>] 128.67K  --.-KB/s    in 0.002s  

2025-12-10 14:23:38 (71.6 MB/s) - ‘redteam_code.zip’ saved [131756/131756]

Archive:  redteam_code.zip
   creating: redteam_code/
  inflating: redteam_code/main.py    
 extracting: redteam_code/requirements.txt  
  inflating: redteam_code/test.csv   
  inflating: redteam_code/train.csv
```

Install dependencies: 
```
pip3 install -r requirements.txt
python3 -c "import nltk; nltk.download('stopwords')"
python3 -c "import nltk; nltk.download('punkt_tab')"
```

In browser - > data poisoning 


<img width="1100" height="630" alt="image" src="https://github.com/user-attachments/assets/20295260-e89f-4c5b-8db2-5466cbb0171e" />

```
head -n 101 training_data.csv > poison-student.csv
```

```
$ sudo nano main.py
```

Changing from line 90
```
└──╼ [★]$ cat main.py 
import pandas as pd
import numpy as np
import re
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from nltk.stem import PorterStemmer
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.naive_bayes import MultinomialNB
from sklearn.pipeline import Pipeline

# -------------------------------------------------------------------
# Data Helper

def preprocess_message(message):
    stop_words = set(stopwords.words("english")) - {"free", "win", "cash", "urgent"}
    stemmer = PorterStemmer()

    message = message.lower()
    message = re.sub(r"[^a-z\s$!]", "", message)
    tokens = word_tokenize(message)
    tokens = [stemmer.stem(word) for word in tokens if word not in stop_words]
    return " ".join(tokens)


def preprocess_dataframe(df):
    df['message'] = df['message'].apply(preprocess_message)
    df = df.drop_duplicates()

    return df

# -------------------------------------------------------------------
# Model Helper

# classify messages by a trained model
def classify_messages(model, msg_df, return_probabilities=False):
    if isinstance(msg_df, str):
        msg_preprocessed = [preprocess_message(msg_df)]
    else:
        msg_preprocessed = [preprocess_message(msg) for msg in msg_df]

    msg_vectorized = model.named_steps["vectorizer"].transform(msg_preprocessed)

    if return_probabilities:
        return model.named_steps["classifier"].predict_proba(msg_vectorized)

    return model.named_steps["classifier"].predict(msg_vectorized)


# train a model on the given data set
def train(dataset):
    # read training data set
    df = pd.read_csv(dataset)

    # data preprocessing
    df = preprocess_dataframe(df)

    # data preparation
    vectorizer = CountVectorizer(min_df=1, max_df=0.9, ngram_range=(1, 2))
    X = vectorizer.fit_transform(df["message"])
    y = df["label"].apply(lambda x: 1 if x == "spam" else 0)

    # training
    pipeline = Pipeline([("vectorizer", vectorizer), ("classifier", MultinomialNB())])
    param_grid = {"classifier__alpha": [0.1, 0.5, 1.0]}
    grid_search = GridSearchCV(pipeline, param_grid, cv=5, scoring="f1")
    grid_search.fit(df["message"], y)
    best_model = grid_search.best_estimator_

    return best_model


# evaluate a given model on our test dataset
def evaluate(model, dataset):
    # read test data set
    df = pd.read_csv(dataset)

    # prepare labels
    df['label'] = df['label'].apply(lambda x: 1 if x == "spam" else 0)

    # get predictions
    predictions = classify_messages(model, df['message'])

    # compute accuracy
    correct = np.count_nonzero(predictions == df['label'])
    return (correct / len(df))

# -------------------------------------------------------------------
# Main
                                                         
model = train("./poison-student.csv")     <------ from here down to the end 

acc = evaluate(model, "./training_data.csv")
print(f"Model accuracy: {round(acc*100, 2)}%")

message = "Hello World! How are you doing?"

predicted_class = classify_messages(model, message)[0]
predicted_class_str = "Ham" if predicted_class == 0 else "Spam"
probabilities = classify_messages(model, message, return_probabilities=True)[0]

print(f"Predicted class: {predicted_class_str}")
print("Probabilities:")
print(f"\t Ham: {round(probabilities[0]*100, 2)}%")
print(f"\tSpam: {round(probabilities[1]*100, 2)}%")

```

Test `main.py`

```
$ python3 main.py 
Model accuracy: 94.56%
Predicted class: Ham
Probabilities:
	 Ham: 98.7%
	Spam: 1.3%
```

Insode the `poison-student.csv` change where ham is to spam 

example: but dont remove all the hams just a portion of them or the model will only have one probability and error. 

<img width="1003" height="710" alt="image" src="https://github.com/user-attachments/assets/6068d9d0-36d7-46c9-b702-740b7194e5a2" />

testing: 

```
└──╼ [★]$ python3 main.py
Model accuracy: 13.71%
Predicted class: Spam
Probabilities:
	 Ham: 5.01%
	 Spam: 94.99%
```

Upload the `poison-student.csv` : 


<img width="965" height="564" alt="image" src="https://github.com/user-attachments/assets/3f56b051-0387-400a-a4bc-c483b59be854" />

flag: 


<img width="871" height="642" alt="image" src="https://github.com/user-attachments/assets/fd77af65-3798-4344-bd5d-b9281902c729" />


Question 3: 

Root folder of the browser --> view page source


<img width="1174" height="641" alt="image" src="https://github.com/user-attachments/assets/2865a440-f6ff-476c-83a5-c7eec3b743d0" />

```
 $ wget http://83.136.249.34:42827/model
--2025-12-10 14:44:48--  http://83.136.249.34:42827/model
Connecting to 83.136.249.34:42827... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1757818 (1.7M) [application/octet-stream]
Saving to: ‘model’

model               100%[===================>]   1.68M  3.11MB/s    in 0.5s    

2025-12-10 14:44:48 (3.11 MB/s) - ‘model’ saved [1757818/1757818]
```
flag : 

```
md5sum model
8007XXXXXXXXXXXXXXXXXX7db02c  model
```









