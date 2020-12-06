random_state=2

without grid search

bnb has an AUC of: 0.631534702191562
gnb has an AUC of: 0.61909818765436
mnb has an AUC of: 0.6368917906920165
dtc has an AUC of: 0.580514430164515
rfc has an AUC of: 0.7834940902039302
mlp has an AUC of: 0.7099560931591158

select rfc as the primary model

rfc with grid search has an AUC of: 
[0.78663673, 0.7860894 , 0.79022205, 0.78819331, 0.79014695]


with extension
array([0.78786725, 0.78425996, 0.78958111, 0.7921241 , 0.79575273])


random_state=1

useFeatures=True

without gridsearch
0.7975
wirh gridsearch
0.8041718870248817


add some features https://www.rdkit.org/docs/source/rdkit.Chem.Fragments.html
without gridsearch
0.804
with
0.8069966164817003

useFeature=True and useFeature=False and with some features https://www.rdkit.org/docs/source/rdkit.Chem.Fragments.html
without gridsearch
0.813144607051296 (0.811 without some features)
and with gridsearch
0.8195

k-Fold
[0.81526082, 0.80167301, 0.8043937 , 0.80420655, 0.80748479]


# Final Result (RF)
RF
* test fingerprint(True)
0.8147589588917745

* test fingerprint(False)
0.8161009945989475

* m2v(No regularization)
0.

* fingerprint(true+false)
0.8294

* fingerprint(true+false) + m2v(No regularization)

