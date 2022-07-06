# Clustering Algorithms: K-Means

## Learning Objectives

* What is K-Means Clustering?
* How does it work?
* Choosing the number of clusters for K-means:
  * Elbow Method
  * Silhouette Method
* Pros and Cons of K-Means



## K-Means Clustering

K-means clustering is one of the simplest and most popular unsupervised machine learning algorithms. You can even say it is _the_ most popular clustering algorithm.

It is intuitive, easy to implement, and fast.

K = number of clusters/groups you want the data to be divided into.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_5d627b3744404f83a4980a968370929c.png)




## How does it work?

K-means is an unsupervised model so the data is unlabeled. But the model mathematically allocates each data point to a cluster.

Here we have some 2-dimensional unlabelled data that looks like below. All the points are of the same colour(green) i.e. they are not segregated into clusters at the moment.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_7c14e8c0aa13414e91c91facfa0a2169.png)



**STEP 0: Decide the number of clusters (K)**

Upon initializing the model, we must pre-decide on a number of clusters. Having to do this in advance is a drawback of the model.

Let’s choose k=2 (a.k.a. 2 clusters) for this example.

**STEP 1:** Randomly create centroids or points that are supposed to be the centers of the clusters (represented by purple). Note that they don’t need to be at the centers initially, they can be placed anywhere.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_04a522026b0d48fb84898eb9374f0c80.png)



**STEP 2:** Each data point is allocated to the nearest centroid:





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_2d3cb58dfccf4b97be06bb07ac1cded9.png)




Initially, our clusters look like below (look at how the data is divided into red and yellow clusters):





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_7ad31e408a6743e980d1ac1473618c32.png)





**STEP 3:** Centroids move to the location of the average of points in their cluster:




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_ff63f02a97b14657b9431ee1e31ec899.png)




**STEP 4:** Repeat allocating each point to the nearest centroid.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_e52ca48df4084fd6b7f23fce3251b4d8.png)




Which gives us clusters according to our second iteration.





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_496388f4c15e4e1babc12401cdc26f40.png)





**STEP 5:** Repeat this process until clusters stop moving

That is, when 2 consecutive times you get the same clusters, there’s no need to repeat the steps.

Is that it?

Yes. Except that we can end up with some pretty poor results if the initial centroid locations are not optimal.

So we repeat this whole process multiple times, and accept the result with the least cumulative variation across clusters.

## Summary



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_b6ed76aace934b0485b9614f5c6a54d9.png)









<iframe width="560" height="315" src="https://www.youtube.com/embed/IJt62uaZR-M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










## K-means Clustering






<iframe width="560" height="315" src="https://www.youtube.com/embed/EItlUEPCIzM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










## Must Try!

This website will allow you to visualise K-Means clustering on your own. At one point, you’ll observe that the centroid has stopped moving and the clusters remain the same. That is when you know that the algorithm has converged and given you the final clusters.

I strongly suggest to spend some time with this tool: [Visualizing k-means Clustering/](https://www.naftaliharris.com/blog/visualizing-k-means-clustering/)





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_0bea076aeb984af2b0d20b6bd7866f3a.png)







## Choosing the number of clusters for K-means

One of the most challenging tasks in this clustering algorithm is to choose the right values of k.

If you are choosing the k values randomly, it might be correct or may be wrong. If you will choose the wrong value then it will directly aﬀect your model performance. So there are two methods by which you can select the right value of k.

1. Elbow Method.
2. Silhouette Method.

Now, Let’s understand both the concepts one by one in detail.

### Elbow Method

Elbow is one of the most well-known methods by which you can select the right value of k and boost your model performance. It is also a bit naïve in its approach.

It is an empirical method to find out the best value of k. It picks up a range of values and takes the best among them. It calculates the sum of the square of the points and calculates the average distance.

Why is it called an ‘elbow’ method, you may ask? That is because the graph plotted in this case resembles an elbow. The value of k falling on the joint part is what we consider to be the optimum value.








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_d61becc396be4407b5a789010c58e37b.png)










![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_17e6e45c8c234a46b4f1657ae4887a0b.png)






Since the graph starts almost straightening out at 3, 3 is the optimum k value according to the elbow method.

### Problems with Elbow Method

Unfortunately, we do not always have such clearly clustered data. This means that the elbow may not be clear and sharp.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_00077dc8d6c0496ca9a485320945828e.png)



For Dataset A, the elbow is clear at k = 3. However, this choice is ambiguous for Dataset B. We could choose k to be either 3 or 4.

In such an ambiguous case, we may use the Silhouette Method.

### Silhouette Method

The silhouette method is somewhat different. Like the elbow method, it also picks up a range of k values and draws the silhouette graph. It calculates the silhouette coefficient of every point.

A higher Silhouette Coefficient score relates to a model with better defined clusters.

For eg. in the 1st graph, you can see that cyan has a higher silhouette coefficient score. It is also the most segregated (better defined) than the other two clusters black and yellow.






![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_3b180f4c2e4d4613ba712a3ce7c81064.png)




Silhouette value measures how similar a point is to its own cluster (cohesion) compared to other clusters (separation).

* The range of the Silhouette value is between +1 and -1.
* A high value is desirable and indicates that the point is placed in the correct cluster.
* If many points have a negative Silhouette value, it may indicate that we have created too many or too few clusters.

We mentioned before that a high Silhouette Score is desirable. **The Silhouette Score reaches its global maximum at the optimal k.** This should ideally appear as a peak in the Silhouette Value-versus-k plot.

Here is one such plot:







![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_5522fc93c8c3455ab80ba0b628b6a2ea.png)







There is a clear peak at k = 3. Hence, it is optimal.

### Note

The Elbow Method is more of a decision rule, while the Silhouette is a metric used for validation while clustering. Thus, it can be used in combination with the Elbow Method.

Therefore, the Elbow Method and the Silhouette Method are not alternatives to each other for finding the optimal K. Rather they are tools to be used together for a more confident decision.

### Implementation of Elbow and Silhouette methods

[Determining the Optimal K for K-Means](https://medium.com/analytics-vidhya/how-to-determine-the-optimal-k-for-k-means-708505d204eb)

This article explains both the Elbow method and the Silhouette score in detail.

## Pros and Cons of K-Means

### Pros:

* Easy to interpret
* Relatively fast
* Scalable for large data sets
* Able to choose the positions of initial centroids in a smart way that speeds up the convergence
* Guarantees convergence

### Cons:

* Number of clusters must be pre-determined. K-means algorithm is not able to guess how many clusters exist in the data. Determining number of clusters may well be a challenging task.
* Can only draw linear boundaries. If there is a non-linear structure separating groups in the data, k-means will not be a good choice.
* Slows down as the number of samples increases because at each step, k-means algorithm accesses all data points and calculates distances.
* Sensitive to outliers

## Notebook

Implementation of K-Means Clustering:

[https://dphi.tech/notebooks/1325/gunnika/implementing-kmeans-clustering-algorithm](https://dphi.tech/notebooks/1325/gunnika/implementing-kmeans-clustering-algorithm)