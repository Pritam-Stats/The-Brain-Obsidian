**Parent Topic** : [[PCA - Principal Component Analysis]]
**Created** : June 11, 2025 | 6:40 AM
**Platform** : #pw #KrishNaik 

---
- PCA is the technique of **Feature Extraction** used for **Dimensionality Reduction**
- Use to remove the [[The Curse of Dimensionality]].
- The problem with Feature Selection was - the loss of information because of completely ignoring some features. So comes PCA.
- PCA works on a process called **Eigen Value Decomposition** of a Covariance Matrix of a dataset.
### Geometrical Intuition
- Consider, to predict the price of a house. 
	- F1 - Size of the house
	- F2 - No. of Rooms
	- 2D dataset. PCA - 2D -> 1D
- First, we draw a vector called **PC1**. And we project the data points on that vector.
	- For n number of features, we can draw n **Principal Components** PC1, PC2,..., PC_n
	- **Each PC will be perpendicular to each other**
	- Then we project the data points on the PCs and calculate the Spread and Variance.
	- And to reduce the dimension to (n-k) we select the top (n-k) features with max spread and variance.
### Objective of PCA
1. 
## Mathematical Intuition
- We create n PCs, PC1, PC2,... PC_n
- $Var(PC_1) > Var(PC_2)$
- **Two important parts of PCA**
	1. Projection - To understand the math behind projecting the data points to the vector which will ultimately become our new data points.
	2. Optimization -  To find the PC with **max Variance**
-   

### Working of PCA
- **Eigen Value Decomposition**- Gives eigen vectors and values
	1. Calculate Covariance matrix between features. $Cov(X_1, X_2) = A$                  $$C = Corr(X_1, X_2) = (\frac{X \cdot X^T}{n-1}) \quad \quad ; X = [X_1-\bar{X_1} \quad X_2-\bar{X_2}], \text{The data set.}$$
	2. We have to standardize the Dataset before applying PCA
	3. Using the following equation we can find Eigen Values $$ \det(C - \lambda I) = 0$$
	4. Now to find the Eigen Vectors from the values $$ C \cdot X = \lambda \cdot X$$
	5. Calculate the Eigen Vectors of the Covariance Matrix$$A \cdot \vec{v} = \lambda \cdot \vec{v}$$
	6. $\vec{v}$ is the Eigen Vector and $\lambda$ is the eigen value. **The Eigen vector with the max eigen value represents the direction in which there will be the max variance.** So this will help identifying the PC1
	7. The Eigen Vector having the next highest value will represent the direction in which the data has the highest remaining variance so that will be PC2.
#### Eigen Vectors and Eigen Values - Linear Transformation
- Visualize linear transformation - [GeoGebra](https://www.geogebra.org/m/YCZa8TAH)
- The direction doesn't change in case of eigen vectors, only get stretched.
	![[Linear_Transformation_Visualization - Eigen Vector.png]]
 

