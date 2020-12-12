# Notes

[See the project](https://github.com/Spycsh/DataScienceNoteBooks/tree/main/projects/modular-activity-prediction-project)

## Data Science Notes from the rdkit challenge

1. To keep training set independent from the testing data, split before data preprocessing (normalization, discretization and imputation)

2. The minmax scaler, imputer should be fit and transform on the training set, and then only transform on the testing set.

3. KFold should be exerted on the whole training set, not the training set obtained by train test(validation) split.

4. AUC calculation

```python
def cal_auc(prob, labels):
    f = list(zip(prob, labels))
    rank = [values2 for values1, values2 in sorted(f, key=lambda x: x[0])]
    rankList = [i + 1 for i in range(len(rank)) if rank[i] == 1]
    posNum = 0
    negNum = 0
    for i in range(len(labels)):
        if (labels[i] == 1):
            posNum += 1
        else:
            negNum += 1
    auc = (sum(rankList) - (posNum * (posNum + 1)) / 2) / (posNum * negNum)
    return auc
```

can also use (note the sequence of the parameters)
```python
from sklearn.metrics import roc_auc_score
auc = roc_auc_score(np.array(y_val), np.array(prediction[:, 1]))
```

## Numpy

numpy vectorization/ broadcast

https://realpython.com/numpy-array-programming/

* random

if we set seed, every time the random number we generated is the same
otherwise, random number is different
```python
import numpy as np
np.random.rand(4) # an array, size of 4
numpy.random.randint(low, high=None, size=None, dtype=int) # [low, high). If high is None (the default), then results are from [0, low)

* merge
```python
a = np.arange(16).reshape(4,4)
b = np.arange(20).reshape(4,5)
np.hstack((a,b))
c = np.arange(30).reshape(6,5)
np.vstack((b,c))
```

* add one column at assigned location

```python
a = np.array([[1,2,3],[4,5,6],[7,8,9]])
b = np.array([[0,0,0]])
c = np.insert(a, 0, values=b, axis=0)
d = np.insert(a, 0, values=b, axis=1)
```

## pandas

* loc, iloc

```python
df = df.loc[0:2, ['A', 'C']]
df = df.iloc[0:2, [0, 2]]
```

* groupby

```python
train_df.groupby('ACTIVE').agg({'num_atoms':'mean'})

train_df.groupby("ACTIVE").agg({'molecule_weights':'max'})

```

* filter/drop columns
```python
train_df.drop(columns=['INDEX','SMILES','ACTIVE'])
df.dropna() # drop the row
df.dropna(axis='columns') # drop the column
df.dropna(how='any')
df.dropna(thresh=2)
```

* select two or more columns
```python
df.loc[:,['Index','NoAtoms']]
df[['Index','NoAtoms']]
```

* convert one column of lists to multiple column of elements

```python
# there is only one column 
df=pd.DataFrame({'col':[[2,3,4], [6,9,0], [7,2,5], [3,5,6]]}, index=list('abcd'))
df1=df['col'].apply(pd.Series,index=['col1','col2','col3'])   # 
```

## python tricks

* zip

```python
a = np.arange(3)
b = np.arange(3)
list(zip(a,b)) # return [(0,0),(1,1),(2,2)]
```

* chain lists
```python
import itertools
vector_lists = list(itertools.chain(*MF_x))
```

faster when number of lists >> 2
