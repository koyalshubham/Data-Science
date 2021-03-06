# 2B

# Main study 

Feature selection is the process of removing irrelevant or redundant features from the original data set. So the execution time of the classifier that processes the data reduces, also accuracy increases because irrelevant features can include noisy data affecting the classification accuracy negatively. With feature selection the understandability can be improved and cost of data handling becomes smaller. 

Feature selection algorithms are divided into three categories; filters, wrappers and embedded selectors. Filters evaluate each feature  independent from the classifier, rank the features after evaluation and take the superior ones. Wrappers takes a subset of the feature set, evaluates the classifier’s performance on this subset, and then another subset is evaluated on the classifier. The subset for which the classifier has the maximum performance is selected. So wrappers are dependent on the selected classifier. In fact wrappers are more reliable because classification algorithm affects the accuracy, although the selection of the subset is an NP-hard problem. So it takes considerable processing time and memory. Some heuristic algorithms can be used for subset selection such as genetic algorithm, greedy stepwise, best first or random search. Therefore, the filters are more time efficient when compared to wrappers, but they don’t take into account that selecting the better features may relevant to classification algorithms. Embedded techniques on the other hand perform feature selection during learning process like artificial neural networks do. 

## Curse of Dimensionality

The curse of dimensionality refers to the phenomenon that many types of data analysis become significantly harder as the dimensionality of the data increases. Specifically, as dimensionality increases, the data becomes increasingly sparse in the space that it occupies. For classification, this can mean that there are not enough data objects to allow the creation of a model that reliably assigns a class to all possible objects. For clustering, the definitions of density and the distance between points, which are critical for clustering, become less meaningful.

In high-dimensional data sets, the traditional Euclidean notion of density, which is the number of points per unit volume, becomes meaningless. To see this, consider that as the number of dimensions increases, the volume increases rapidly, and unless the number of points grows exponentially with the number of dimensions, the density tends to 0. Also, proximity tends to become more uniform in high-dimensional spaces. Another way to view this fact is that there are more dimensions (attributes) that contribute to the proximity between two points and this tends to make the proximity more uniform. Since most clustering techniques are based on proximity or density, they can often have difficulty with high-dimensional data. One approach to addressing such problems is to employ dimensionality reduction techniques as discussed below.

In machine learning problems that involve learning a "state-of-nature" from a finite number of data samples in a high-dimensional feature space with each feature having a range of possible values, typically an enormous amount of training data is required to ensure that there are several samples with each combination of values. A typical rule of thumb is that there should be at least 5 training examples for each dimension in the representation. With a fixed number of training samples, the predictive power of a classifier or regressor first increases as number of dimensions/features used is increased but then decreases, which is known as Hughes phenomenon or peaking phenomena.

### Combinatorial Explosion

Combinatorial explosion is a fundamental problem in computing. It is the problem that the number of combinations that one has to examine grows exponentially, so fast that even the fastest computers will require an intolerable amount of time to examine them. The combinatorial explosion problem limits the ability of computers to solve large problems. This is because in most realistic problems of interest to us, the number of combinations is typically very large.

Suppose you have n decisions to make and for each decision, you have 10 possible options. Then you will have all together 10 to the power n combinations of solutions. The number of combinations grows exponentially as n increases.

In chess, one could examine every possible move and their subsequent moves. However, if we assume that there are 20 choices per move, then looking ahead 15 moves will involve examination of 20 to the power 15, or 3.3x10^19, sequences. If our computer manages to examine 1,000,000,000 sequences per second (be sure that your desktop computer won't have that speed), a brute force search would have to take over 90 million hours ( over 10,000 years) to make one move, which is obviously unacceptable. To improve the speed of play, one needs either much faster computers or clever algorithms which allows one to be highly selective in what sequences to examine. The combinatorial explosion problem prevented computers from competing with human world champions until recently.

One of the main thrusts of artificial intelligence work has been to find ways, such as heuristic search, to circumvent the combinatorial explosion.

### Distance concentration

Distance concentration is the phenomenon that, as the data dimensionality increases, all the pairwise distances (dissimilarities) may
converge to the same value. The lack of contrast between the nearest and the furthest points affects each area where high-dimensional data processing is required — e.g. high-dimensional data analysis, database indexing & retrieval, data analysis, statistical machine learning. 

The similarity-based reasoning that machine learning algorithms depend on (explicitly or implicitly) breaks down in high dimensions. Consider a nearest neighbor classifier with Hamming distance as the similarity measure, and suppose the class is just x1 ∧ x2. If there are no other features, this is an easy problem. But if there are 98 irrelevant features x3, . . . , x100, the noise from them completely
swamps the signal in x1 and x2, and nearest neighbor effectively makes random predictions. Even more disturbing is that nearest neighbor still has a problem even if all 100 features are relevant! This is because in high dimensions all examples look alike. Suppose, for
instance, that examples are laid out on a regular grid, and consider a test example X(t). If the grid is d-dimensional, X(t)’s 2d nearest examples are all at the same distance from it. So as the dimensionality increases, more and more examples become nearest neighbors of X(t), until the choice of nearest neighbor (and therefore of class) is effectively random.

<INSERT Feature Selection>

## Variable ranking technique

Variable Ranking is the process of ordering the features by the value of some scoring function, which usually measures feature-relevance. Resulting set: The score S(fi) is computed from the training data, measuring some criteria of feature fi. By convention a high score is indicative for a valuable (relevant) feature.

A simple method for feature selection using variable ranking is to select the k highest ranked features according to S. This is usually not optimal, but often preferable to other, more complicated methods. It is computationally efficient — only calculation and sorting of n scores.

In this text we will be covering three variable ranking techniques namely
  1. Correlation Criteria
  2. Information Theoretic Ranking Criteria
  3. Single Variable Classifiers

### Correlation Criteria

The correlation coefficient is a measure of the strength of a linear association between two variables and is denoted by r. Basically, a Pearson product-moment correlation attempts to draw a line of best fit through the data of two variables, and the Pearson correlation coefficient, r, indicates how far away all these data points are to this line of best fit (i.e., how well the data points fit this new model/line of best fit).

The correlation coefficient, r, can take a range of values from +1 to -1. A value of 0 indicates that there is no association between the two variables. A value greater than 0 indicates a positive association; that is, as the value of one variable increases, so does the value of the other variable. A value less than 0 indicates a negative association; that is, as the value of one variable increases, the value of the other variable decreases. This is shown in the diagram below:

![Correlation Criteria](https://statistics.laerd.com/statistical-guides/img/pearson-1-small.png)

The stronger the association of the two variables, the closer the Pearson correlation coefficient, r, will be to either +1 or -1 depending on whether the relationship is positive or negative, respectively. Achieving a value of +1 or -1 means that all your data points are included on the line of best fit – there are no data points that show any variation away from this line. Values for r between +1 and -1 (for example, r = 0.8 or -0.4) indicate that there is variation around the line of best fit. The closer the value of r to 0 the greater the variation around the line of best fit. Different relationships and their correlation coefficients are shown in the diagram below:

![Various R Values](https://statistics.laerd.com/statistical-guides/img/pearson-2-small.png)

### Information Theoretic Ranking Criteria

The current practice to designing ranking criteria can be viewed as heuristic “bottom-up” approaches—manually construct a criterion composed of various terms, that attempt to balance relevance against redundancy at each step, with the expectation that it should have a desirable effect on our overall objective. Two variables that are useless by themselves can be useful together. This is achieved by Information Theoritic Ranking Criteria. 

![Information Theoretic Ranking Criteria](https://cdn-images-1.medium.com/max/675/1*927GxAiWjdGQSptS_gpM0Q.png)

It relies on empirical estimates of the mutual information between each variable and the target:

![Formula](https://i.imgur.com/J2qF1fx.png)

where p(x) and p(y) are the probability densities of x and y, and p(x, y) is the joint density. The criterion I (i) is a measure of dependency between the density of variable xi and the density of the target y.

![Comparision](https://cdn-images-1.medium.com/max/1350/1*VlU6Oo-tlMC0jr-bToezhA.png)

### Single Variable Classifiers

Using correlation criteria as a ranking criterion for regression enforces a ranking according to goodness of linear fit of individual variables. One can extend to the classification case the idea of selecting variables according to their individual predictive power, using as criterion the performance of a classifier built with a single variable. For example, the value of the variable itself (or its negative, to account for class polarity) can be used as discriminant function. A classifier is obtained by setting a threshold q on the value of the variable (e.g., at the mid-point between the center of gravity of the two classes). The predictive power of the variable can be measured in terms of error rate. 

In the case where there is a large number of variables that separate the data perfectly, ranking criteria based on classification success rate cannot distinguish between the top ranking variables. One will then prefer to use a correlation coefficient or another statistic like the margin (the distance between the examples of opposite classes that are closest to one another for a given variable).
