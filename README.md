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
    The <i>i<sup>th</sup></i> tuple (2) contains <i>n</i> attribute values denoted by <i>x<sub>i,j</sub></i> and a target value denoted by <i>y<sub>i</sub></i>.
    Each column index <i>j</i> represents a unique attribute.
    The target value <i>y<sub>i</sub></i> must be at the last index of each tuple.
    A subset of the data set is denoted by <i>S</i> (3).
</p>

<hr>
<p align="center">
    <img src="photos/equations/equation1.png" width=50%>
</p>

<p align="justify">
    Splitting an attribute a
</p>

<p align="center">
    <img src="photos/equations/equation2.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation3.png" width=50%>
</p>
<hr>

<hr>
<p align="center">
    <img src="photos/equations/equation4.png" width=50%>
</p>
<hr>

<hr>
<p align="center">
    <img src="photos/equations/equation5.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation6.png" width=50%>
</p>
<hr>

<hr>
<p align="center">
    <img src="photos/infoEntropy.png" width=70%>
</p>
<hr>

<hr>
<p align="center">
    <img src="photos/equations/equation7.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation8.png" width=50%>
</p>
<hr>

<hr>
<p align="center">
    <img src="photos/equations/equation9.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation10.png" width=50%>
</p>
<hr>

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
