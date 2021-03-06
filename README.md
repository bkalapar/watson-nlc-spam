# watson-nlc-spam

<img src="https://raw.githubusercontent.com/cdimascio/watson-nlc-spam/master/assets/watson-nlc.png"  width="200"  align="right" /></br>

Create a spam classifier with Watson Natural Language Classifier. This repo provides code samples and instruction to support the IBM developerWorks article, ["Create a natural language classifier that identifies spam"](https://www.ibm.com/developerworks/library/cc-spam-classification-service-watson-nlc-bluemix-trs/index.html).

Learn how to train a spam classfier, validate its accuracy, classify new texts, and run it as a web application. You'll do it all with Watson Natural Language Classifier.

### Watch the Tutoral Video

[![Watch the tutorial video](https://raw.githubusercontent.com/cdimascio/watson-nlc-spam/master/assets/poster.png)](https://www.youtube.com/watch?v=upK42t7Ojls&feature=youtu.be)

This project contains:

* Training data

* Test data

* a Python script to measure accuracy

## What you'll need

### Prerequisites

* [Python](https://www.python.org/downloads/)

* [curl](http://curl.haxx.se/download.html)

* [IBM Cloud Account](www.bluemix.net)

* An instance of the Watson Naturual Language Classifier service on IBM Cloud (see
  blog)

## How is this repo organized

#### Layout

* `data/SpamHam-Train.csv` - SpamHam training data

* `data/SpamHam-Test.json` - SpamHam test data

* `spam.py` - a python script used to measure the accuracy of the classifier

* `web/` - The node.js based web demo (http://watsonnlcspam.mybluemix.net)

#### The data

Data files are a transform of [SMS Spam Collection
v.1](<<http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/> >)[ (UCI's SMS
Spam Collectoin Data
Set](https://archive.ics.uci.edu/ml/datasets/SMS+Spam+Collection))

## How-To

See the ["Create a natural language classifier that identifies spam"](https://www.ibm.com/developerworks/library/cc-spam-classification-service-watson-nlc-bluemix-trs/index.html) developerWorks article for details or (for less detail) follow the general outline below.

#### Create a NL Classifier instance on IBM Cloud

* Go to [IBM Cloud](www.bluemix.net)
* From the IBM Cloud catalog, select Watson Natural Language Classifier

#### Train the NL classifier using Spam/Ham data

Training the classifier is easy. Simply, provide training data in a Watson NLC
compatible format and POST a request to the Watson NLC `/classifiers` REST
endpoint.

* Open`data/SpamHam-Train.csv` to view the data format
* Train Watson NLC

    ```
  curl -X POST -u username:password -F training_data=@SpamHam-Train.csv \
   -F training_metadata="{\"language\":\"en\",\"name\":\"My Classifier\"}" \
  "https://gateway.watsonplatform.net/natural-language-classifier/api/v1/classifiers"
    ```

#### Measure Accuracy of the Spam classifier

* Open `spam.py` and supply values for:
  _ `YOUR_CLASSIFIER_ID`
  _ `YOUR_CLASSIFIER_USERNAME` \* `YOUR_CLASSIFIER_PASSWORD`

* Run `pip install requests`

* Run `python spam.py`

## About the Data

Use [Watson Natural Language Classifier](https://www.ibm.com/watson/services/natural-language-classifier/) to predict spam. The training data is a public set of 5,574 English SMS messages collected for mobile phone spam research.

The SMS Spam Collection v.1 is a public set of SMS labeled messages that have been collected for mobile phone spam research. It has one collection composed by 5,574 English, real and non-encoded messages, tagged according being legitimate (ham) or spam. More information can be found here.

More information can be found
[here](http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/)

A comprehensive study of this data can be found in the following papers:

* Almeida, T.A., Gómez Hidalgo, J.M., Yamakami, A. Contributions to the Study
  of SMS Spam Filtering: New Collection and Results. Proceedings of the 2011
  ACM Symposium on Document Engineering (DOCENG'11), Mountain View, CA, USA, 2011.
  ([preprint](http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/doceng11.pdf))

* Gómez Hidalgo, J.M., Almeida, T.A., Yamakami, A. On the Validity of a New
  SMS Spam Collection. Proceedings of the 11th IEEE International Conference
  on Machine Learning and Applications (ICMLA'12), Boca Raton, FL, USA, 2012.
  ([preprint](http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/icmla12.pdf))

* Almeida, T.A., Gómez Hidalgo, J.M., Silva, T.P. Towards SMS Spam Filtering:
  Results under a New Dataset. International Journal of Information Security
  Science (IJISS), 2(1), 1-18. (Invited paper - [full
  version](http://www.dt.fee.unicamp.br/~tiago/smsspamcollection/IJISS13.pdf))

## Links

* [Medium article - by Zia Mohammad](https://medium.com/ibm-watson/identify-spam-with-watson-natural-language-classifier-42f273d310f4)
* [developerWorks article - by Carmine DiMascio](https://www.ibm.com/developerworks/library/cc-spam-classification-service-watson-nlc-bluemix-trs/index.html)

## License

[Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)

Copyright 2015-2018 Carmine M DiMascio

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
