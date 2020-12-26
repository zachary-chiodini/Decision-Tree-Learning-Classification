<h1>Decision Tree Learning Classification</h1>
<p align="justify">
    This is a naive C4.5 algorithm used for classification of data written in Python.
</p>

<p align="left">
    <img src="photos/dependencies.png" width="244px">
</p>

<h1>Mathematics</h1>

<p align="justify">
    The module "decision_tree.py" interprets a data set <i>R</i> as a set of <i>m</i> tuples (1), where each tuple is an example.
    The <i>i<sup>th</sup></i> tuple (2) contains <i>n</i> attribute values denoted by <i>x<sub>i,j</sub></i> (where <i>j = 1, 2, ..., n</i>) 
    and a target value denoted by <i>y<sub>i</sub></i>.
    Each index <i>j</i> represents a unique attribute.
    The target value <i>y<sub>i</sub></i> must be at the last index of each tuple.
    A subset of the data set is denoted by <i>S</i> (3).
</p>

<hr>
<p align="center">
    <img src="photos/equations/equation1.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation2.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation3.png" width=50%>
</p>
<hr>

<p align="justify">
    Each attribute and its distinct values will be a node in the decision tree. 
    An attribute's unique values will be its child nodes,
    and each of these child nodes will then be a parent node to another attribute node, and so on.
    This continues until the target value is reached, which is a leaf node.
    The module "decision_tree.py" splits an attribute <i>a</i> into its unique values by creating a new set <i>X<sub>a</sub></i>,
    which contains values <i>x<sub>i,j</sub></i> in each tuple <i>S<sub>i</sub></i> for all tuples in the subset <i>S</i>
    such that <i>j = a</i> (4). A set of unique target values <i>y<sub>i</sub></i> in subset <i>S</i> is also defined (5).
</p>

<hr>
<p align="center">
    <img src="photos/equations/equation4.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation5.png" width=50%>
</p>
<hr>

<p align="justify">
    Deciding which attribute should be chosen as a root node or a child node of another attribute's value is determined partly 
    by the information entropy <i>H</i> of the subset <i>S</i> (6),
    where <i>P(S,y)</i> is the probability of selecting the target value <i>y</i> from the subset <i>S</i> (7),
    or the number of times the value <i>y</i> occurs in the subset <i>S</i> devided by the number of examples in the subset <i>S</i>.
    The vertical bars denote the cardinality of the set or sequence.
    The value of the information entropy is between 0 and 1 bits inclusive.
</p>

<hr>
<p align="center">
    <img src="photos/equations/equation6.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation7.png" width=50%>
</p>
<hr>

<p align="justify">
    A plot of the information entropy of a set containing two target values, <i>+</i> for positive or yes and <i>-</i> for negative or no, 
    and their probabilities, <i>p<sub>+</sub></i> and <i>p<sub>-</sub></i> respectively, over all possible probabilities is shown below.
    When the number of positive values is the same as the number of negative values in the set, the information entropy is one.
    When the set contains only positive values or only negative values, the information entropy is zero.
    Therefore, a set with a lower information entropy is preferred, because it is closer to achieving a final verdict of yes or no.
    Note that <i>p<sub>+</sub> = 1 - p<sub>-</sub></i>.
</p>

<hr>
<p align="center">
    <img src="photos/infoEntropy.png" width=70%>
</p>
<hr>

<p align="justify">
    The information entropy provides a measure of the purity of a data set, or how close it is to achieving a final verdict,
    but it alone does not provide information on which attributes should be prioritized when selecting nodes to construct the decision tree.
    For this, the purity of the data set after an attribute is split on each of its values should be measured and compared with the purity of the unsplit data set.
    This calculation is called the information gain <i>IG</i> (8), 
    which is the change in information entropy of a subset <i>S</i> after splitting an attribute <i>a</i>.
    The information entropy of the split is given by a weighted sum of the information entropy of each subset 
    <i>S<sub>a</sub>(S,x)</i> (9), which contains tuples <i>S<sub>i</sub></i> with the split value <i>x</i> at <i>x<sub>i,a</sub></i>.
</p>

<hr>
<p align="center">
    <img src="photos/equations/equation8.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation9.png" width=50%>
</p>
<hr>

<p align="justify">
    The ID3 algorithm uses information gain to select nodes when constructing the tree.
    The C4.5 algorithm uses the information gain ratio <i>IGR</i> (10), 
    which is the information gain upon splitting an attribute <i>a</i> devided by the intrinsic value <i>IV</i> of the split (11).
    The information gain ratio takes the cardinality of the split into account when choosing an attribute.
    The larger the portion of data eliminated by the split, 
    the smaller the cardinality of <i>S<sub>a</sub>(S,x)</i>, the larger the instrisic value, and the smaller the information gain ratio.
    This way, attributes that do not contribute very much to the decision making process but split into pure data sets will be of less priority.
</p>
<p align="justify">
    Note that when the instrinsic value is zero, the data set cannot be split anymore and a final verdict must be achieved by a majority vote.
    The module "decision_tree.py" returns an information gain ratio of zero if an intrinsic value of zero is encountered.
    This is reasonable because the information gain should also be zero if the intrisnsic value is zero.
    However, a majority vote is taken just in case the information gain is not zero.
</p>

<hr>
<p align="center">
    <img src="photos/equations/equation10.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation11.png" width=50%>
</p>
<hr>

<p align="justify">
    The module "decision_tree.py" uses the algorithm described in pseudocode below.
    This is a naive C4.5 algorithm.
</p>

<hr>
<p align="center">
    <img src="photos/algorithm.png" width=63%>
</p>
<hr>
<h1>Try It</h1>

```python
from decision_tree import DecisionTree
```


```python
model = DecisionTree()
model.importcsv( 'tennis.csv' )
```

```python
model.label
```

    ['Outlook', 'Humidity', 'Wind', 'Play']

```python
model.data
```

    {('Overcast', 'High', 'Strong', 'Yes'),
     ('Overcast', 'High', 'Weak', 'Yes'),
     ('Overcast', 'Normal', 'Strong', 'Yes'),
     ('Overcast', 'Normal', 'Weak', 'Yes'),
     ('Rain', 'High', 'Strong', 'No'),
     ('Rain', 'High', 'Weak', 'Yes'),
     ('Rain', 'Normal', 'Strong', 'No'),
     ('Rain', 'Normal', 'Weak', 'Yes'),
     ('Sunny', 'High', 'Strong', 'No'),
     ('Sunny', 'High', 'Weak', 'No'),
     ('Sunny', 'Normal', 'Strong', 'Yes'),
     ('Sunny', 'Normal', 'Weak', 'Yes')}


```python
model.learn( model.data )
model.plot( 'Will Peter Play Golf?' )
```


![png](photos/tennistree.png)

```python
model = DecisionTree()
model.importcsv( 'mushrooms.csv' )
len( model.data )
```




    8124




```python
model.label
```




    ['cap shape',
     'cap surface',
     'cap color',
     'bruises',
     'odor',
     'gill attachment',
     'gill spacing',
     'gill size',
     'gill color',
     'stalk shape',
     'stalk root',
     'stalk surface above ring',
     'stalk surface below ring',
     'stalk color above ring',
     'stalk color below ring',
     'veil type',
     'veil color',
     'ring number',
     'ring type',
     'spore print color',
     'population',
     'habitat',
     'class']




```python
model.testAndTrain( ratio = 0.25 )
```

    Samples in training set:  2031
    Samples tested         :  6093
    Total samples          :  8124
    Model accuracy         :  99.61 %

```python
model.plot()
```

<p align="center">
    <img src="photos/mushroomtree.png" width=100%>
</p>
