Unsupervised Image Clustering on CIFAR-10

This project was developed as part of my MSc in Digital Media and Computational Intelligence at AUTH. It explores how we can group images into categories (like airplanes, cars, or animals) without using any pre-existing labels, relying purely on the data's structure.

The Approach

The main challenge with the CIFAR-10 dataset is the high dimensionality of the images. To make the data manageable, I implemented a pipeline that reduces complexity while trying to keep the most important relationships intact:

Dimensionality Reduction: I used Isomap to project the 3,072-dimensional image data into just 2 dimensions. I chose Isomap because it's effective at capturing the non-linear "manifold" of image data.

Clustering: For the grouping, I applied Spectral Clustering (using nearest neighbors). This method works well when clusters have complex shapes that standard algorithms like K-Means might miss.

The Mapping Problem: Since clustering is unsupervised, the labels produced (0-9) don't naturally match the real classes. I used the Hungarian Algorithm (linear_sum_assignment) to find the best possible mapping between my clusters and the ground truth labels.

Analysis & Results

I evaluated the model using several metrics:

Accuracy: Around 19.8%. While this might seem low for a supervised task, for a completely unsupervised approach on raw pixels, it shows that the model is successfully picking up on basic visual patterns.

Clustering Quality: I tracked ARI (Adjusted Rand Index) and Homogeneity to see how "pure" the clusters were.

K-Behavior: I also ran an analysis on different values of K to see how the clustering stability changes as we increase the number of groups.

Tech used
Python (Scikit-learn, NumPy, Matplotlib)

TensorFlow/Keras (strictly for dataset loading)
