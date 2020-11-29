# Notes

numpy vectorization/ broadcast

https://realpython.com/numpy-array-programming/

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

* chain lists
```python
import itertools
vector_lists = list(itertools.chain(*MF_x))
```

faster when number of lists >> 2
