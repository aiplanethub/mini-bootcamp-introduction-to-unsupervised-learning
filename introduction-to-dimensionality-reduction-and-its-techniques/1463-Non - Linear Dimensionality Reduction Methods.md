# Non-Linear Dimensionality Reduction Methods

## Learning Objectives

* Non-linear Dimensionality Reduction Methods
* Kernel PCA
* t-distributed Stochastic Neighbor Embedding (t-SNE)
* Self-Organizing Map (SOM)

## Non-linear Dimensionality Reduction Methods

Non-linear transformation methods, also known as **manifold learning methods**, are used when the data doesn’t lie on a linear subspace. It is based on the **manifold hypothesis**, which says that **in a high dimensional structure, most relevant information is concentrated in a small number of low dimensional manifolds**.

If a linear subspace is a flat sheet of paper, then a rolled-up sheet of paper is a simple example of a non-linear manifold. Informally, this is called a Swiss roll, a canonical problem in non-linear dimensionality reduction.

Some popular manifold learning methods are:

1. **Multi-Dimensional scaling (MDS):** A technique used for analyzing the similarity or dissimilarity of data as distances in geometric spaces. Projects data to a lower dimension such that data points close to each other (in terms of Euclidean distance) in the higher dimension are also close in the lower dimension.
2. **Isometric Feature Mapping (Isomap):** Projects data to a lower dimension while preserving the geodesic distance (rather than Euclidean distance as in MDS). Geodesic distance is the shortest distance between two points on a curve.
3. **Locally Linear Embedding (LLE):** Recovers global non-linear structure from linear fits. Each local patch of the manifold can be written as a linear, weighted sum of its neighbors given enough data.
4. **Hessian Eigenmapping (HLLE):** Projects data to a lower dimension while preserving the local neighborhood like LLE but uses the Hessian operator (a mathematical operator you don’t need to worry about right now) to achieve this result better, hence the name.
5. **Spectral Embedding (Laplacian Eigenmaps):** Uses spectral techniques to perform dimensionality reduction by mapping nearby inputs to nearby outputs. It preserves locality rather than local linearity.
6. **t-distributed Stochastic Neighbor Embedding (t-SNE):** Computes the probability that pairs of data points in the high-dimensional space are related and then chooses a low-dimensional embedding that produces a similar distribution.

Kernel PCA, Isomap, and many more...

Didn’t understand the basic definitions completely?

No worries, we’ll now elaborate on some popularly used Non-Linear Dimensionality Reduction methods.

## Kernel PCA

We’ve read about PCA till now. PCA is a linear method. That is, we can only apply it to linearly separable datasets. It does an excellent job for linearly separable datasets. But, many real-world datasets are not linearly separable. So if we use it on non-linear datasets, we might get a result that is not optimal.

Kernel PCA uses a kernel function to project the dataset into a higher dimensional feature space, where it is linearly separable. It is similar to the idea of Support Vector Machines.

There are various kernel methods like linear, polynomial, and gaussian.

### The “magic” of high dimensions

* Given some problem, how do we know what classes of functions are capable of solving that problem?
* VC (Vapnik-Chervonenkis) theory tells us that often mappings that take us into a higher dimensional space than the dimension of the input space provide us with greater classification power.
* Problem: These classes are linearly inseparable in the input space. (in 2 dimensions)








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_60f7da0f84ff4c0380ec1b7440fc61aa.png)












* Solution: High-Dimensional Mapping. We can make the problem linearly separable by a simple mapping: (from 2 dim to 3 dim)








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a3691d792e334938aca67bce71073519.png)









### Kernel Trick

High-dimensional mapping can seriously increase computation time. The question is, can we get around this problem and still benefit from high dimensions? Yes! Using the Kernel Trick.

The kernel trick is a method to project original data into a higher dimension without sacrificing too much computational time (Non-linear feature mapping).

Some popular kernels are:

* Gaussian
* Polynomial
* Hyperbolic Tangent

### Kernel PCA

Now coming to the main part, what is Kernel PCA?

Kernel PCA extends conventional principal component analysis (PCA) to a high dimensional feature space using the “kernel trick.”

With this, you can extract up to n (number of samples) non-linear principal components without expensive computations.

### Kernel PCA Implementation

Below you can see a sample implementation of Kernel PCA. The kernel used here is linear, but there are many useful kernels you might want to try out.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_eb3a3cc4fda54f5080bb812cfd6d3c85.png)




## t-distributed Stochastic Neighbor Embedding (tSNE)

t-Distributed Stochastic Neighbor Embedding (t-SNE) is a non-linear technique for dimensionality reduction that is particularly well suited for the **visualization of high-dimensional datasets**. It is extensively applied in image processing, NLP, genomic data, and speech processing.

Until recently, it was the best, state-of-the-art dimensionality reduction technique. Now, it has been replaced by a better and faster method called **UMAP**.

t-SNE basically reduces the multi-dimensional data into 2 or 3 dimensions such that the human eyes can visualize it. This reduces the data analysis work as it can reveal various patterns in the data set in 2d or 3d.

### Visualizing 784 dimensions in 2d using t-SNE




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_5761cdb22ed54e529b9fd9950c4ce692.png)





### t-SNE Detailed Explanation










<iframe width="560" height="315" src="https://www.youtube.com/embed/NEaUSP4YerM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>











### t-SNE Implementation in Python

t-SNE is present as a package in sklearn’s manifold library. A simple implementation of t-SNE will look something like the below code snippet. We’ll dive into the details of the implementation in the notebook.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_d5adf9fd19604da3a6155473acf006dc.png)



### t-SNE Strengths

* **Works well for Non-Linear data:** It can interpret the relationship between features, regardless of how complex it is.
* **Preserves Local and Global Structure:** t-SNE can preserve the data’s local and global structure. Therefore, points close by in the high-dimensional dataset also tend to be close in the low dimension dataset.

### t-SNE Weakness

* **Dimensionality reduction for other purposes:** t-SNE is only useful for visualizing high-dimensional data. It is not useful for other purposes of dimensionality reduction, like feature selection or extraction.
* **Curse of intrinsic dimensionality (sensitive to intrinsic dimension):** Intrinsic Dimension is the no. of variables needed to generate a good approximation of the signal. t-SNE performs poorly if the high dimensional data actually has high intrinsic dimensionality.
* **Non-convexity of the t-SNE cost function:** we must choose several optimization parameters.

### t-SNE Resources

Here’s an amazing article you can go through to understand t-SNE in detail: [https://towardsdatascience.com/what-why-and-how-of-t-sne-1f](https://towardsdatascience.com/what-why-and-how-of-t-sne-1f78d13e224d) [78d13e224d](https://towardsdatascience.com/what-why-and-how-of-t-sne-1f78d13e224d)

## Self-Organizing Map (SOM) or Self-Organizing Feature Map (SOFM)

A self-organizing map (SOM) is a type of artificial neural network (ANN) that is trained using unsupervised learning to produce a **low-dimensional (typically two-dimensional), discretized representation of the input space of the training samples**, called a **map**, and is, therefore, a method to perform dimensionality reduction.

Self-organizing maps diﬀer from other artificial neural networks as they apply **competitive learning** as opposed to error-correction learning (such as backpropagation with gradient descent), and in the sense that they use a neighborhood function to preserve the topological properties of the input space.

SOM was introduced by Finnish professor Teuvo Kohonen in the 1980s and is sometimes called a **Kohonen map**.

The video below gives a simple intuition about Self Organizing Maps by connecting its working to several applications.

Feel free to skip the part ‘Breaking Down the Weight Update Formula’; it gets a little mathematical there.





<iframe width="560" height="315" src="https://www.youtube.com/embed/g8O6e9C_CfY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>






### SOM Implementation in Python

While you can code SOM from scratch in Python, the package of choice for easily using self-organizing maps in Python is minisom: [https://github.com/JustGlowing/minisom](https://github.com/JustGlowing/minisom)

It is a simple, Numpy-based implementation of the Self-Organizing Maps and is very user-friendly. It can be installed using: `pip install minisom`.

### Resources for understanding SOM in depth

* [How SOM (Self Organizing Maps) algorithm works](https://youtu.be/H9H6s-x-0YE)
* [SOM Tutorial](https://algobeans.com/2017/11/02/self-organizing-map/)

### Notebook

[Implementation of various linear and non-linear dimensionality reduction techniques](https://dphi.tech/notebooks/1326/gunnika/comparison-of-various-dimensionality-reduction-techniques-in-python)