# Decision Tree Learning Classification
Naive C4.5 Algorithm

<p align="center">
    <img src="photos/equations/equation1.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation2.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation3.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation4.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation5.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation6.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation7.png" width=50%>
</p>

<p align="center">
    <img src="photos/infoEntropy.png" width=70%>
</p>

<p align="center">
    <img src="photos/equations/equation8.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation9.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation10.png" width=50%>
</p>

<p align="center">
    <img src="photos/equations/equation11.png" width=50%>
</p>

<p align="center">
    <img src="photos/algorithm.png" width=63%>
</p>

```python
from decision_tree import DecisionTree
```


```python
model = DecisionTree()
model.importcsv( 'tennis.csv' )
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
model.label
```




    ['Outlook', 'Humidity', 'Wind', 'Play']




```python
model.learn( model.data )
model.plot( 'Will Peter Play Golf?' )
```


![png](tennistree.png)
