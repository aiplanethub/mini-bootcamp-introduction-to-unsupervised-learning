# Auto-Encoders for Dimensionality Reduction

## Learning Objectives

* Introduction to Auto-encoders
* Components of Auto-encoders
* Example of Image reconstruction with dimensionality reduction
* Applications of Auto-encoders

### Auto-encoders

Another popular dimensionality reduction method that gives spectacular results are auto-encoders, a type of artificial neural network that aims to copy their inputs to their outputs.

Its procedure starts compressing the original data into a shortcode ignoring noise. Then, the algorithm uncompresses that code to generate an image as close as possible to the original input.

### Components of Auto-encoders

An autoencoder is composed of two parts :

1. **Encoder:** compresses the input into a latent-space representation.
2. **Decoder:** reconstruct the input from the latent space representation.








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_31821184c4704ca9984c38a85e5ec41f.png)








### Example of Image reconstruction with dimensionality reduction










![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_65260c1901344a6f91756c6c79883704.png)









You might notice that the reconstructed images are a little blurry and not so detailed. But, they still retain the same structure.

### Applications of Auto-encoders

* Dimensionality Reduction
* Image Compression
* Image Denoising
* Feature Extraction
* Image generation
* Sequence to sequence prediction
* Recommendation system

### Autoencoder








<iframe width="560" height="315" src="https://www.youtube.com/embed/Rdpbnd0pCiI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>






### Additional Resources

Autoencoders involve the concept of Deep Learning. So make sure you’re familiar with it before starting with implementation of Autoencoders. We’ll not be diving into it at the moment. If you want an introduction to Deep Learning, consider checking out our [Getting Started with Deep Learning Course.](https://dphi.tech/courses/getting-started-with-deep-learning) It's free!

[Implementation of Autoencoders on MNIST Dataset](https://pub.towardsai.net/autoencoders-for-dimensionality-reduction-6fb6553f392f)