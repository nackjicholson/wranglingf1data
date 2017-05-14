

```python
import os
import pandas as pd
```


```python
os.getcwd()
```




    '/Users/nackjicholson/repos/wranglingf1data'




```python
# Making a list
['Hamilton', 'Rosberg', 'Vettel', 'Ricciardo', 'Alonso', 'Raikkonen', 'Button', 'Magnussen']
```




    ['Hamilton',
     'Rosberg',
     'Vettel',
     'Ricciardo',
     'Alonso',
     'Raikkonen',
     'Button',
     'Magnussen']




```python
# Loading a Dataframe from an online csv
url = 'https://gist.githubusercontent.com/psychemedia/11187809/raw/31f8deab586322514b375ef581e83c909ab12d3c/winners2014start.csv'
winners = pd.read_csv(url)
winners
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>carNum</th>
      <th>pos</th>
      <th>driverId</th>
      <th>constructorId</th>
      <th>grid</th>
      <th>fastlaptime</th>
      <th>fastlaprank</th>
      <th>race</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>1</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>92.478</td>
      <td>1</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>2</td>
      <td>kevin_magnussen</td>
      <td>mclaren</td>
      <td>4</td>
      <td>93.066</td>
      <td>6</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22</td>
      <td>3</td>
      <td>button</td>
      <td>mclaren</td>
      <td>10</td>
      <td>92.917</td>
      <td>5</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>3</th>
      <td>44</td>
      <td>1</td>
      <td>hamilton</td>
      <td>mercedes</td>
      <td>1</td>
      <td>103.066</td>
      <td>1</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>103.960</td>
      <td>2</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>3</td>
      <td>vettel</td>
      <td>red_bull</td>
      <td>2</td>
      <td>104.289</td>
      <td>4</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>6</th>
      <td>44</td>
      <td>1</td>
      <td>hamilton</td>
      <td>mercedes</td>
      <td>2</td>
      <td>97.108</td>
      <td>2</td>
      <td>Bahrain</td>
    </tr>
    <tr>
      <th>7</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>1</td>
      <td>97.020</td>
      <td>1</td>
      <td>Bahrain</td>
    </tr>
    <tr>
      <th>8</th>
      <td>11</td>
      <td>3</td>
      <td>perez</td>
      <td>force_india</td>
      <td>4</td>
      <td>99.320</td>
      <td>7</td>
      <td>Bahrain</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Column selection
# driverId as a pd.Series
winners['driverId']
```




    0            rosberg
    1    kevin_magnussen
    2             button
    3           hamilton
    4            rosberg
    5             vettel
    6           hamilton
    7            rosberg
    8              perez
    Name: driverId, dtype: object




```python
# Select a new dataframe with only the driverId column
winners[['driverId']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>driverId</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>rosberg</td>
    </tr>
    <tr>
      <th>1</th>
      <td>kevin_magnussen</td>
    </tr>
    <tr>
      <th>2</th>
      <td>button</td>
    </tr>
    <tr>
      <th>3</th>
      <td>hamilton</td>
    </tr>
    <tr>
      <th>4</th>
      <td>rosberg</td>
    </tr>
    <tr>
      <th>5</th>
      <td>vettel</td>
    </tr>
    <tr>
      <th>6</th>
      <td>hamilton</td>
    </tr>
    <tr>
      <th>7</th>
      <td>rosberg</td>
    </tr>
    <tr>
      <th>8</th>
      <td>perez</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Setting carNum to an enumerable Category type, instead of int64 type
winners['carNum'] = winners['carNum'].astype('category')
winners['carNum']
```




    0     6
    1    20
    2    22
    3    44
    4     6
    5     1
    6    44
    7     6
    8    11
    Name: carNum, dtype: category
    Categories (6, int64): [1, 6, 11, 20, 22, 44]



[More on Pandas Categories](http://pandas.pydata.org/pandas-docs/stable/categorical.html)


```python
winners['carNum'].cat.categories
```




    Int64Index([1, 6, 11, 20, 22, 44], dtype='int64')




```python
# Statistical information about the winners dataframe
winners.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pos</th>
      <th>grid</th>
      <th>fastlaptime</th>
      <th>fastlaprank</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>9.000000</td>
      <td>9.000000</td>
      <td>9.000000</td>
      <td>9.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2.000000</td>
      <td>3.333333</td>
      <td>98.136000</td>
      <td>3.222222</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.866025</td>
      <td>2.738613</td>
      <td>4.805507</td>
      <td>2.333333</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>92.478000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>93.066000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2.000000</td>
      <td>3.000000</td>
      <td>97.108000</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3.000000</td>
      <td>4.000000</td>
      <td>103.066000</td>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>3.000000</td>
      <td>10.000000</td>
      <td>104.289000</td>
      <td>7.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
winners.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>carNum</th>
      <th>pos</th>
      <th>driverId</th>
      <th>constructorId</th>
      <th>grid</th>
      <th>fastlaptime</th>
      <th>fastlaprank</th>
      <th>race</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>1</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>92.478</td>
      <td>1</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>2</td>
      <td>kevin_magnussen</td>
      <td>mclaren</td>
      <td>4</td>
      <td>93.066</td>
      <td>6</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22</td>
      <td>3</td>
      <td>button</td>
      <td>mclaren</td>
      <td>10</td>
      <td>92.917</td>
      <td>5</td>
      <td>Australia</td>
    </tr>
  </tbody>
</table>
</div>




```python
winners.columns
```




    Index(['carNum', 'pos', 'driverId', 'constructorId', 'grid', 'fastlaptime',
           'fastlaprank', 'race'],
          dtype='object')




```python
# Vectorized Computation with dataframes
tmp = pd.DataFrame({'origcol': list('abc')})
tmp
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>origcol</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b</td>
    </tr>
    <tr>
      <th>2</th>
      <td>c</td>
    </tr>
  </tbody>
</table>
</div>




```python
tmp['newcol'] = 1
tmp
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>origcol</th>
      <th>newcol</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>c</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
tmpShape = tmp.shape
tmpShape
```




    (3, 2)




```python
numRows = tmpShape[0]
numRows
```




    3




```python
numRowsAlt = len(tmp.index)
numRowsAlt
```




    3




```python
# newcol2 is a row number column that starts at 1 instead of 0
tmp['newcol2'] = range(1, numRows + 1)
tmp
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>origcol</th>
      <th>newcol</th>
      <th>newcol2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>a</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>c</td>
      <td>1</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
winners2 = winners.copy()
```


```python
winners2['posdelta'], winners2['poslapdelta'] = [winners2['grid'] - winners2['pos'], winners2['fastlaprank'] - winners2['pos']]
```


```python
winners2.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>carNum</th>
      <th>pos</th>
      <th>driverId</th>
      <th>constructorId</th>
      <th>grid</th>
      <th>fastlaptime</th>
      <th>fastlaprank</th>
      <th>race</th>
      <th>posdelta</th>
      <th>poslapdelta</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>1</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>92.478</td>
      <td>1</td>
      <td>Australia</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>2</td>
      <td>kevin_magnussen</td>
      <td>mclaren</td>
      <td>4</td>
      <td>93.066</td>
      <td>6</td>
      <td>Australia</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22</td>
      <td>3</td>
      <td>button</td>
      <td>mclaren</td>
      <td>10</td>
      <td>92.917</td>
      <td>5</td>
      <td>Australia</td>
      <td>7</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Filtering dataframes
winners[(winners['pos'] == 2) | (winners['pos'] == 3)]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>carNum</th>
      <th>pos</th>
      <th>driverId</th>
      <th>constructorId</th>
      <th>grid</th>
      <th>fastlaptime</th>
      <th>fastlaprank</th>
      <th>race</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>2</td>
      <td>kevin_magnussen</td>
      <td>mclaren</td>
      <td>4</td>
      <td>93.066</td>
      <td>6</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22</td>
      <td>3</td>
      <td>button</td>
      <td>mclaren</td>
      <td>10</td>
      <td>92.917</td>
      <td>5</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>103.960</td>
      <td>2</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>3</td>
      <td>vettel</td>
      <td>red_bull</td>
      <td>2</td>
      <td>104.289</td>
      <td>4</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>7</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>1</td>
      <td>97.020</td>
      <td>1</td>
      <td>Bahrain</td>
    </tr>
    <tr>
      <th>8</th>
      <td>11</td>
      <td>3</td>
      <td>perez</td>
      <td>force_india</td>
      <td>4</td>
      <td>99.320</td>
      <td>7</td>
      <td>Bahrain</td>
    </tr>
  </tbody>
</table>
</div>




```python
winners[winners['pos'] != 1]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>carNum</th>
      <th>pos</th>
      <th>driverId</th>
      <th>constructorId</th>
      <th>grid</th>
      <th>fastlaptime</th>
      <th>fastlaprank</th>
      <th>race</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>2</td>
      <td>kevin_magnussen</td>
      <td>mclaren</td>
      <td>4</td>
      <td>93.066</td>
      <td>6</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22</td>
      <td>3</td>
      <td>button</td>
      <td>mclaren</td>
      <td>10</td>
      <td>92.917</td>
      <td>5</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>103.960</td>
      <td>2</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>3</td>
      <td>vettel</td>
      <td>red_bull</td>
      <td>2</td>
      <td>104.289</td>
      <td>4</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>7</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>1</td>
      <td>97.020</td>
      <td>1</td>
      <td>Bahrain</td>
    </tr>
    <tr>
      <th>8</th>
      <td>11</td>
      <td>3</td>
      <td>perez</td>
      <td>force_india</td>
      <td>4</td>
      <td>99.320</td>
      <td>7</td>
      <td>Bahrain</td>
    </tr>
  </tbody>
</table>
</div>




```python
winners['pos'] != 1
```




    0    False
    1     True
    2     True
    3    False
    4     True
    5     True
    6    False
    7     True
    8     True
    Name: pos, dtype: bool




```python
winners[['driverId','race','pos']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>driverId</th>
      <th>race</th>
      <th>pos</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>rosberg</td>
      <td>Australia</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>kevin_magnussen</td>
      <td>Australia</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>button</td>
      <td>Australia</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>hamilton</td>
      <td>Malaysia</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>rosberg</td>
      <td>Malaysia</td>
      <td>2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>vettel</td>
      <td>Malaysia</td>
      <td>3</td>
    </tr>
    <tr>
      <th>6</th>
      <td>hamilton</td>
      <td>Bahrain</td>
      <td>1</td>
    </tr>
    <tr>
      <th>7</th>
      <td>rosberg</td>
      <td>Bahrain</td>
      <td>2</td>
    </tr>
    <tr>
      <th>8</th>
      <td>perez</td>
      <td>Bahrain</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
winners[winners['pos']==1][['driverId', 'race']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>driverId</th>
      <th>race</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>rosberg</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>3</th>
      <td>hamilton</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>6</th>
      <td>hamilton</td>
      <td>Bahrain</td>
    </tr>
  </tbody>
</table>
</div>




```python
winners.sort_values(by='carNum')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>carNum</th>
      <th>pos</th>
      <th>driverId</th>
      <th>constructorId</th>
      <th>grid</th>
      <th>fastlaptime</th>
      <th>fastlaprank</th>
      <th>race</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>3</td>
      <td>vettel</td>
      <td>red_bull</td>
      <td>2</td>
      <td>104.289</td>
      <td>4</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>1</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>92.478</td>
      <td>1</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>3</td>
      <td>103.960</td>
      <td>2</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>7</th>
      <td>6</td>
      <td>2</td>
      <td>rosberg</td>
      <td>mercedes</td>
      <td>1</td>
      <td>97.020</td>
      <td>1</td>
      <td>Bahrain</td>
    </tr>
    <tr>
      <th>8</th>
      <td>11</td>
      <td>3</td>
      <td>perez</td>
      <td>force_india</td>
      <td>4</td>
      <td>99.320</td>
      <td>7</td>
      <td>Bahrain</td>
    </tr>
    <tr>
      <th>1</th>
      <td>20</td>
      <td>2</td>
      <td>kevin_magnussen</td>
      <td>mclaren</td>
      <td>4</td>
      <td>93.066</td>
      <td>6</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22</td>
      <td>3</td>
      <td>button</td>
      <td>mclaren</td>
      <td>10</td>
      <td>92.917</td>
      <td>5</td>
      <td>Australia</td>
    </tr>
    <tr>
      <th>3</th>
      <td>44</td>
      <td>1</td>
      <td>hamilton</td>
      <td>mercedes</td>
      <td>1</td>
      <td>103.066</td>
      <td>1</td>
      <td>Malaysia</td>
    </tr>
    <tr>
      <th>6</th>
      <td>44</td>
      <td>1</td>
      <td>hamilton</td>
      <td>mercedes</td>
      <td>2</td>
      <td>97.108</td>
      <td>2</td>
      <td>Bahrain</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
