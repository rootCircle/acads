- Machine Learning: Input Data -> Program
- Train -> Data + Target Attribute
- Test -> Actual Value : Predicted Value
- Over-fitting: Too many features
- Under-fitting: Very less features
- ### Feature Selection Methods
	- #### Filter Method - Coorelation coefficient
		- If a feature and target variable are related, else remove them
	- #### Wrapper Method
		- ##### Recursive feature elimination
			- Try all permutations, and then eliminate with highest accuracy
			- Expensive to calculate
	- #### Embedded Method - Decision Tree
		- Don't suffer from over-fitting like in wrapper
- ### Classifier
	- Gives possibility (+1/-1) and _probability_(used in tie breaker for positives) of a class(target value) from feature
	- ![image.png](../assets/image_1731839209147_0.png)
	- One vs All
		- No. of classifier = no. of class
	- One vs one
		- Combination of Pair of class
		- No of classifier = n(n-1)/2 where n=no. of class
- ### Principle Component Analysis
	- Reduce dimension by changing POV
	- Principle Component should be independent of each other (orthogonal) and priority in order (PC1 > PC2 ......)
	- Covariance matrix /Eigen vector/matrix
		- ![image.png](../assets/image_1726673748216_0.png)
		- ![image.png](../assets/image_1726674151969_0.png){:height 296, :width 406}
	- Covariance -> |$C-\lambda I$| = 0 -> CV = $\lambda$V (where V is eigen vector= [x1 y1]) -> assume y1 = 1 and find x1 -> y1 = $$y1/\sqrt{x^2+y^2}$$ & x1 = $$x1/\sqrt{x^2+y^2}$$
- ### Confusion Matrix
	- Pred X vs Actual Y NO, YES
	- Recall = True-Positive/Actual Yes
	- Precision = True-Positive/Predicted-Yes
	- Accuracy = Correct Prediction/Total
	- f1 score = Harmonic mean of Precision and Recall
	- Error = 1 - Accuracy
	- Type I -> False Positive
	- Type II error -> False Negative
- ### Curse of dimensionality
	- Threshold after which accuracy start to decrease
- ### Managing missing record
	- Remove record
	- Create sub-model (if feature A is missing, then make a sub-model with A as target variable)
	- Mean, Median, Mode
- ### Categorical Data
	- One hot encoding(all in 1 & 0) -> Dummy encoding(eliminate 1st or last feature) -> Effect Coding scheme(-1 if all are 0)
- ### Regression Classification
	- Outliers: Extremities (less effective features on target)
	- Multi-colinearity: Independent variable are co-related
	- #### Linear Regression
		- Continuous linear relationship
		- ![image.png](../assets/image_1726701262861_0.png)
		- y = bx + a (or more x -> multiple linear Reg) [a,b are regression coeff]
	- #### Logistic Regression
		- Dependent variable is binary (true or false, 0 or 1)
		- Uses probability
		- Sigmoid
			- $1/(1+e^{-x})$
			- Logit R -> have a cutoff at 0.5
- ### Naive Bayes Classifier
	- ![image.png](../assets/image_1726680767344_0.png){:height 218, :width 541}
	- Feature set F = {$y_1, y_2, y_3$}, then find $x_i(\in X)$ $\ni$ $P(F|x_i) = P(y_1|x_i) P(y_2|x_i) P(y_3|x_i)$ is maximum
	- Variants (Not in syllabus)
	  collapsed:: true
		- ![image.png](../assets/image_1731861174617_0.png){:height 413, :width 565}
		- Gaussian - continuous feature value
- ### Support Vector Machines
	- ![image.png](../assets/image_1726703190452_0.png)
	- Marginal plane should be max separated and equidistant from best fit line
	- ![image.png](../assets/image_1726703413595_0.png){:height 319, :width 342}
	- Cost function: Maximise 2/|w|
	- Loss function: MInimise |w|/2
		- ![image.png](../assets/image_1726704185828_0.png){:height 257, :width 472}
	- #### Regression
		- ![image.png](../assets/image_1726704259886_0.png){:height 201, :width 488}
		- ![image.png](../assets/image_1726704537556_0.png){:height 107, :width 478}
	- SVM Kernel -> add dimension to reduce confusion (can't classify in hyperplane can be be classified in higher dimension)
		- ![image.png](../assets/image_1726704736143_0.png)
- ### KNN
	- ![image.png](../assets/image_1726706869373_0.png){:height 163, :width 542}
- ### Decision tree
	- ![image.png](../assets/image_1726707311541_0.png){:height 291, :width 745}
	- Make tree by order of Gain (Feature) [highest first]
- ### DBSCAN
	- Density based
	- \epsilon radius circle must have atleast 3 three point within => centre = core point
	- if a circle from point contain core point (but point \ne core point), then point is boundary point -> considered in same cluster
	- if none of both then noise point (outliers)
- ### K means algorithm
	- Take two points as centroid
	- Calculate euclidean distance for third point from both centroid
	- Take smaller distance as criteria for cluster
	- Recalculate centroid of cluster = midpoint(old_centroid, new_point) other centroid remains same
- ### Hierarchical Clustering
	- #### Divisive
		- ABCDE => (AB) (CDE) => (A) (B) (CD) (E) => A B C D E
	- #### Agglomerative
		- Opposite of divisive, cluster and fuse
		- ##### Simple linkage
			- Take min of distance from distance matrix and fuse point (eg P23 is smallest then fuse 2,3 and then recalculate distance matrix with P23 as new member)
				- The smallest (here 2,3) will form a cluster at distance d, represented on dendogram
				- The distance of Pk from P23 will be dist(Pk, P23) = min{dist(Pk, P2), dist(Pk, P3)}
		- ##### Complete Linkage
			- Same as simple linkage but here distance dist(Pk, P23) = max{dist(Pk,P2), dist(Pk, P3)}