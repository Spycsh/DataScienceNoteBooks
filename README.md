# Notes

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
```
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

* chain lists
```python
import itertools
vector_lists = list(itertools.chain(*MF_x))
```

faster when number of lists >> 2
