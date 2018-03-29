参考Github上使用SVM进行垃圾短信分类的例子，实现的基于朴素贝叶斯进行垃圾短信分类

##reference

[https://github.com/ZPdesu/Spam-Message-Classifier-sklearn]

# Spam-Message-Classification
Classification of spam messages with Naive Bayes by scikit-learn
## Intro to spam message
The task is to classify spam messages which are composed of Chinese characters, English, Numbers and some special characters. 
Normal messages should be identified as 0, and spam messages as 1.

Snapshoot of training data : `RawData/junk_message.txt`

```
0	但是没有首都的在CBD一家好吃
0	今天给大家介绍一款Bookbook电脑包
1	亲爱的家长朋友你们好，我是张老师:新学期现在开始报名啦！本学期对老生家长的义务宣传有个回馈活动，老生带一个新生报名，赠送老生二百元兴趣
0	浙江宁波市马路突然爆裂
1	各位亲们好，新世纪奉节店迎接三八节，贝因美奶粉全场x.x折，欢迎惠额。活动时间x月x日至x月x日。
```

## Prerequisite
* [Python 2.7.x](https://www.python.org/downloads/)
* [Scikit-learn](http://scikit-learn.org/stable/documentation.html#)
* [jieba](https://github.com/fxsjy/jieba)


进入项目文件夹下，从RawData/junk_message.txt中加载原始数据，进行文本域和标签域分割，转存到对应json文件中

```
$ cd Spam-Message-Classification
$ python load_data.py
```

对短信文本进行筛选和处理转换后进行分词，将生成的词向量稀疏矩阵存入Data/word_vector.mtx，词向量对应的词表存入Data/vector_type.json，
标签信息存入`Data/train_label.json

```
$ python word_vector.py
```

将详细的信息，如词表，词向量对应的词表索引，标签信息等存入MongoDB数据库

```
$ python Mongo_Configure.py

**In**

```
$ python bayes_Trainer.py


## Structure

```
├── Naive_Bayes
│   ├── Bayes_Trainer.py
│   ├── Bayes_Trainer.pyc
│   ├── Bayes_Predictor.py
│   ├── Bayes_Predictor.pyc
│   ├── Bayes_Evaluator.py
│   ├── __init__.py
│   ├──result 
│   │  └──predict_label.txt
│   └── output
│       ├── Bayes.pkl
│       └── Terminal.pkl
├── Mongo_Configure.py
├── load_tata.py
├── load_tata.pyc
├── word_vector.py
├── word_vector.pyc
├── preprocessing.py
├── preprocessing.pyc
├── test.py
├── RawData
│   ├── junk_message.txt
│   ├── message.txt
│   ├── train_label.json
│   └── train_content.json
└── Data
    ├── train_label.json
    ├── vector_type.json
    └── word_vector.mtx
```
# spam-message-classification
