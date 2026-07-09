2026-07-08 17:25

#Machine-Learning 

> How do we get more data?

Label unlabeled data.
# Augment data 
Generate new data from existing data. The new data must be relevant to our test set (real data).
# Synthesize data
Use computers to generate data.
# Transfer learning
Train a [[Neural Network]] on a very large dataset (supervised pretraining), then take its parameters to use for our specific case. We need to retrain the output layer or the entire thing if there is sufficient data (fine tuning).