# 2B

Feature selection is the process of removing irrelevant or redundant features from the original data set. So the execution time of the classifier that processes the data reduces, also accuracy increases because irrelevant features can include noisy data affecting the classification accuracy negatively. With feature selection the understandability can be improved and cost of data handling becomes smaller. 

Feature selection algorithms are divided into three categories; filters, wrappers and embedded selectors. Filters evaluate each feature  independent from the classifier, rank the features after evaluation and take the superior ones. Wrappers takes a subset of the feature set, evaluates the classifier’s performance on this subset, and then another subset is evaluated on the classifier. The subset for which the classifier has the maximum performance is selected. So wrappers are dependent on the selected classifier. In fact wrappers are more reliable because classification algorithm affects the accuracy, although the selection of the subset is an NP-hard problem. So it takes considerable processing time and memory. Some heuristic algorithms can be used for subset selection such as genetic algorithm, greedy stepwise, best first or random search. Therefore, the filters are more time efficient when compared to wrappers, but they don’t take into account that selecting the better features may relevant to classification algorithms. Embedded techniques on the other hand perform feature
selection during learning process like artificial neural networks do. 

## Curse of Dimensionality

The curse of dimensionality refers to the phenomenon that many types of
data analysis become significantly harder as the dimensionality of the data
increases. Specifically, as dimensionality increases, the data becomes increasingly
sparse in the space that it occupies. For classification, this can mean
that there are not enough data objects to allow the creation of a model that
reliably assigns a class to all possible objects. For clustering, the definitions
of density and the distance between points, which are critical for clustering,
become less meaningful.

In high-dimensional data sets, the traditional Euclidean
notion of density, which is the number of points per unit volume,
becomes meaningless. To see this, consider that as the number of dimensions
increases, the volume increases rapidly, and unless the number of points grov/s
exponentially with the number of dimensions, the density tends to 0. Also, proximity
tends to become more uniform in high-dimensional spaces. Another way to
view this fact is that there are more dimensions (attributes) that contribute to
the proximity between two points and this tends to make the proximity more
uniform. Since most clustering techniques are based on proximity or density,
they can often have difficulty with high-dimensional data. One approach to
addressing such problems is to employ dimensionality reduction techniques.
