- Consider a dataset with 50 features, to predict house price. 
	- M1 - Trained with top 3 features. Acc - A1
	- M2 - Trained with top 15 features. Acc - A2 > A1
	- M3 - Trained with top 20 feature. Acc - A3 > A2
- Now suppose we keep on feeding the model with less important features, then we will notice that the respective models with higher no. of **lesser-important** features will perform worse than M1 M2. The accuracy will get decreased. Because the model will be **Overfeeded** with unnecessary information. This is known as the [[Curse of Dimensionality]]
### Ways to remove the curse of dimensionality
1. [[Feature Selection]]
	- It's simple, here we only select the top k most important features and ignore the rest.
2. Dimensionality Reduction [[PCA - Principal Component Analysis]] - This is a Feature Extraction technique.
	- PCA is a method to reduce the feature dimension without comprising the loss of data. For example, from 500 features we transform the feature to 20 features. We use Eigen Values, eigen vectors. We don't completely ignore the other features, we extract some information from the rest of the features.