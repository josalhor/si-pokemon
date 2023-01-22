# Introduction
This repository hosts the code for the third deliverable of the subject.
The authors are:

- [Joan Palau Oncins](https://github.com/JoanPalau)
- [Josep Maria salvia Hornos](https://github.com/josalhor)

# Challanges
The most challanging parts have been:
1. Analysing the attributes and determine which one's to take
2. Thinking out of the box in orther to preprocess the information in order to correct the data, improve the data or aggregate the data
3. Once the train score was above the 85% accuracy, each iteration provided few upgrades, overfitting was really easy and you gainned score in the train data and decreased in the test data.

# General comments
## Encodings
## Data preprocessing
## Attribute selection
## Models
Our first approach was to compare between the following models
- DecisionTreeClassifier
- RandomForestClassifier
- MLPClassifier
We finally discarted the first model as it was less performant than the RandomForestClassifier and both of them take the "same" aproach. However, the DecisionTreeClassifier model granted us the possibility to see how was the classification being done with the following code:
```python

from sklearn import tree
from sklearn.tree import DecisionTreeClassifier
from sklearn.model_selection import train_test_split, cross_val_score

from matplotlib import pyplot as plt

dtc_model = DecisionTreeClassifier(criterion="entropy", max_depth=3, min_samples_leaf=5, random_state=42)
dtc_model.fit(X_train_encoded, y_train)
'Train Score', dtc_model.score(X_train_encoded, y_train)

plt.figure(figsize=(30, 20))
tree.plot_tree(dtc_model, class_names=["False", "True"], feature_names=DropTransformer.KEEP_COLUMNS)
plt.show()
```
The result was seeing that the tree only cared about the speed, and that unless the depth was considerable (overfitting), other features would not influence the output of it.