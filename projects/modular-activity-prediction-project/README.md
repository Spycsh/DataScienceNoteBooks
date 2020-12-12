# modular-activity-prediction-project

This is the course project of KTH ID2214. The goal is to extract features of SMILES compounds, build and train models with existing training data to predict modular activity of unknown compounds.

The best AUC score so far is 0.831, with the following settings.

|Model|Features|
|:---:|:---:|
|RandomForestClassifier(max_depth=30, n_estimators=400, class_weight='balanced_subsample')|Basic molecular features + ECFP+FCFP fingerprints (see PPT or thesis)|

> Notice

The result is not the best this year. There is an obvious reason that we do not adopt all the training data but just 80% of it into training the final model because of train-test-split process (20% validation set). Actually with more training data we find that the model has a much better performance. To improve it, you can probably:  

1. train on 100% of the training data to get the model (although someone may say it is unsafe because no validation set is considered but for competition, after you tune the parameters and your model works soundly and well, feel free to use it)

2. further use of GridSearch to tune parameters such like min_sample_split and min_sample_leaf (slow but useful).

3. Try more features by using Rdkit packages. We found that it is useless to drop some features no matter with PCA or other methods. Therefore, you can use more features not fearing of curse of dimensions as long as you have enough time to train.

4. For speed. Perhaps GPU is the best if you have one on your computer. Kaggle is another good choice as it has big storage and good kernal. Colab is not so good because it only can have 8GB free RAM which means that you need to upload your dataset every time you restart your colab (Google drive seems good but is much slower as it is not stored in the RAM of Colab so time latency to access data exists).