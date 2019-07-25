# Ship Type Detection
This project summarizes the outcome of taking part in the computer vision competition organized by Analytics Vidhya (under the name Game of Deep Learning) in which the participants were to determine the type of a ship (out of 5 different ship types) given solely its photograph. It is evident that this competition was all about a multi-class classification problem.

Here is the link to the competition website: https://datahack.analyticsvidhya.com/contest/game-of-deep-learning/#problem_statement.

## Short Description
The Jupyter notebooks are numbered for easier navigation. The first notebook is devoted to the preprocessing of the data to make it usable by models. The next two notebooks contain the actual model training, while in the last one we apply a very simple ensembling procedure to boost the performance of the most promising models.

Our best model achieved the weighted average F1 score of approximately 0.9570 on the offcially binding private leaderboard (where the maximal score of 1.0 represents the perfect prediction).

## More Detailed Description
The preprocessing part consists of splitting the available training data into the training (75% of observations) and validation (25% of observations) sets, homogenizing the dimiensions of the photographs, and applying some further model specific preprocessing.

The model training is divided into two parts. Many models were tried but eventually we settled on the models based on the VGG16 architecture. 

In the first part we used the VGG16 convolutional part (we set the layers in this part to be non-trainable) with a custom trainable fully connected layers. During model training we used data augmentation techniques to help fight overfitting as well as appropriately computed class weights to alleviate the problem of class imbalances. This model achieved the score of about 0.9155 on the public leaderboard, and served as a basis for further fine-tuning performed in the second part of the training. 

In the second part we again used the VGG16 convolutional part (but this time with its last 13 layers set to be trainable) and we attached the fully connected layers trained in the first part. As before, we used data augmentation and precomputed class weights. After the model finished training we selected two most promissing versions from different epochs and combined them into the final model (as described in the last notebook). 

This final model achieved the score of about 0.9627 on the public leaderboard, however, its private leaderboard score was approximately 0.9570.
