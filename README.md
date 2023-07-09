# basic image processing project
this project demonstrates the implementation of basic digital image processing techniques using python and the opencv library.this project  is part of kaizen group task  in basic digital image processing workshop and consist of :
-  read and show image
-  add noise to image
-  apply spatial and frequency filter on noisy image
-  point processing
-   image comperssion

as a memeber of kaizen team, i focuse on applying filter on noisy image and want to share every things i learnt. in  following, you find about:
- How to install and run the project
- Additional information:
  + Noise generation 
  + Image denoising:
    +  Spatial filter
    + Application of  spatial filters
	   + Result of using spatial filters on a image
    + Frequency filter
    + Application of  frequency  filters
	    + Result of using spatial filters on a image
- Reference
- Useful linke
#### How to Install and Run the Project
 the project includes a image and core file, which relies on an utils.py file . to use this project, follow the steps bellow:
 1. install opencv
 2. clone the repository: clone this github repository using the following command:
``git clone``
3. navigate to the project directory: use the **cd** command to move into the project directory:``cd``


#### Noise Generation 
the project provides different types of noise to simulate real-world image degradation. these include:
1. **Gaussian noise**: gaussian noise is a type of statistical noise that follows a gaussian distribution. it can be added to an image by randomly generating pixel values with gaussian-distributed intensity variations.

2. **Salt and pepper noise**: salt and pepper noise is a type of impulse noise that manifests as randomly occurring white and black pixels. it simulates sudden, random intensity spikes or drops in the image.

3. **Poisson noise**: poisson noise is a type of noise that typically occurs in low-light images. it is caused by the random arrival of photons and results in a grainy appearance.

The image after different noises are added to it:
![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/output3.jpg)


#### Image Denoising

we considered two approaches for denoising images to be corrupt by different types of noise: spatial filtering and frequency filtering.

#### spatial filtering
spatial filters are a class of filters used in digital image processing to modify the pixel values of an image based on their spatial neighborhood. 
- **Median filter** 
median filtering is a non-linear smoothing method that replaces each pixel with the median value of its surrounding pixels, effectively reducing the impact of noise while preserving the image's edges and details. since the shot noise value usually lies well outside the true values in the neighborhood, the median filter is able to filter away such bad pixels. able to filter away such bad pixels.
one downside of the median filter, in addition to its moderate computational cost, is that since it selects only one input pixel value to replace each output pixel, it is not as efficient at averaging away regular gaussian noise. 
- **Mean filter:**  
the mean filter replaces each pixel value with the average value of its surrounding pixels. it smoothes the image and reduces high-frequency noise and sharp transitions. this filter is useful for blurring and noise reduction. reduces high-frequency noise and sharp transitions. smoothing is used to reduce irrelevant detail in an image,
where “irrelevant” refers to pixel regions that are small with respect to the size of
the filter kernel.

### Application of  Spatial Filter:
the choice of a spatial filter depends on the specific image processing task and the characteristics of the image and noise. here are some guidelines to consider:

**Noise Reduction:**  median filters are commonly used. median filters are effective against impulse noise.

**Image Enhancement:** filters like the unsharp mask and high-pass filters can be used to enhance image details and edges.

it's important to note that the application of spatial filters is not limited to grayscale images. they can also be applied to each color channel of a color image to achieve desired effects.
the choice of a spatial filter may require experimentation and tuning to achieve the desired results. understanding the underlying concepts and characteristics of each filter will help you make informed decisions and achieve better image processing outcomes.
#### Result of Using spatial filters on a image:
you can see, addaptive filter do not have good performance on Guassian noise, pepper and salt, speckle noise and in poisson noise even add the more noise and it seems mean filter be more successful to reduce Guassian noise than median filter. Both of median and mean filter could reduce paper and salt noise, after using median filter, although, the image is getting more transparent but some salt noise similar the white points remain in for ground. on image with speckle noise, mean filter has better performance at removing noise.


**1.  Spatial filter on image with Guassian noise**:

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/mean-guassian.jpg)

**2.  Spatial filter on image with pepper and salt noise**:

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/output5.jpg)

**3.  Spatial filter on image with poisson noise**:

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/output6.jpg)

**4.  Spatial filter on image with speckle noise**:

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/output7.jpg)

### Frequency Filter:
in image processing, a frequency filter is a technique used to modify the frequency content of an image. it operates in the frequency domain, which is obtained by performing a mathematical transformation called the [fourier transform](https://en.wikipedia.org/wiki/fourier_transform) on the image. the frequency domain represents the image as a combination of different frequencies.
frequency filters can be broadly categorized into two types: high-pass filters and low-pass filters.

- **High-pass filters**: high pass filter removes the low frequency components that means it keeps high frequency components. it is used for sharpening the image. it is used to sharpen the image by attenuati high-pass filters are often used to enhance the edges or details in an image. they can help sharpen an image by emphasizing the high-frequency variations. examples of high-pass filters include the [laplacian filter](https://docs.opencv.org/3.4/d5/db5/tutorial_laplace_operator.html) and [the unsharp mask filter](https://en.wikipedia.org/wiki/unsharp_masking).

- **Low-pass filters**: low pass filter removes the high frequency components that means it keeps low frequency components. low-pass filters are used to remove noise and blur an image by smoothing out the high-frequency details. they are also employed for downsampling or reducing the resolution of an image. examples of low-pass filters include the gaussian filter and the mean filter.
- **Band pass filter:**
band pass filter removes the very low frequency and very high frequency components that means it keeps the moderate range band of frequencies. band pass filtering is used to enhance edges while reducing the noise at the same time


##### Applications of Frequency Filters in Image Processing:

- **Image enhancement:** high-pass filters are used to emphasize edges and details in an image, making it appear sharper and more visually appealing. they are commonly employed in tasks such as image sharpening and contrast enhancement.

- **Noise reduction**: low-pass filters are effective in reducing noise in an image. by attenuating high-frequency noise components, these filters can help to improve the overall image quality and make it more visually pleasing.

- **Image smoothing**: low-pass filters can be used to blur or smooth an image by suppressing high-frequency details. this can be useful in applications like image denoising, image compression, or reducing the resolution of an image. to read more about image smoothing techniques see the [opencv websit](https://en.wikipedia.org/wiki/gaussian_filter).

- **Image compression:** frequency filters play a significant role in image compression techniques like jpeg. by removing high-frequency components that contribute less to the perceptual quality of an image, the file size can be reduced while maintaining acceptable visual fidelity.

- **Feature extraction:** frequency filters can be used in image analysis tasks to extract specific features or patterns. for example, using filters that are sensitive to certain orientations, such as gabor filters, can help detect specific textures or edges in an image.

these are just a few examples of the applications of frequency filters in image processing. the specific choice of filter and its parameters depend on the desired image manipulation or analysis task at hand.

#### Result of runnig cod on a image
you can see the effect of applying filters on noisey image. After change the parameter in filters, there performance improve. For example, in high pass filter reduction reduic from 100 to 50, show better result but the reduction under 50 dont effect on denoising any more. This alsocould be seen in other filters.

1. Low pass filter on guassian noise

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/low-pass%20on%20guassian.jpg)

2. High pass on guassian

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/high%20pass%20on%20guassian.jpg)

3. Frequency on guassian

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/frequencies%20on%20guassian.jpg)

4. frequency on speckle

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/frequencies%20on%20speckel%201.jpg)
 
 after change parameter:

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/frequencies%20on%20speckle%202.jpg)
5. Frequency on salt and pepper
![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/frequencies%20on%20salt%20and%20pepper%201.jpg)

Afrter change parameter:

![](https://github.com/mahboube-askarian/Basic-DIP-Project/blob/main/Result/Image/frequencies%20on%20pepper%20and%20salt%202.jpg)


The choice of the most suitable filter for image denoising depends on the type of noise present in the image. Here's a general guideline for different types of noise:

**Salt and pepper noise**: Salt and pepper noise is a type of impulsive noise characterized by randomly occurring white and black pixels. It simulates the effect of random and isolated errors in the image. Filters such as the median filter or adaptive median filter are effective in removing salt and pepper noise while preserving edges and details in the image.

**Poisson noise**: Poisson noise is typically encountered in images acquired using low-light imaging systems, such as medical imaging or astronomical imaging. It is caused by the random nature of photon arrivals. For denoising images affected by Poisson noise, filters like the Poisson noise reduction filter or the non-local means filter can be utilized. These filters are designed to handle the statistical properties of Poisson noise and yield good denoising results.

**Speckle noise:** Speckle noise is commonly found in images obtained from ultrasound imaging, synthetic aperture radar (SAR), or laser imaging systems. It appears as granular noise that degrades the image quality. Filters like the Lee filter, Frost filter, or the adaptive filter (e.g., adaptive Wiener or adaptive median) are often used for denoising speckle noise. These filters exploit the statistical characteristics of speckle noise to reduce its impact while preserving image features.

It's important to note that the choice of the denoising filter depends on the specific characteristics of the noise and the desired trade-off between noise reduction and preservation of image details. Different filters may perform differently in various scenarios, so it's often recommended to experiment with multiple filters and choose the one that best suits the specific image and noise characteristics.




#### Reference:
- Computer Vision: Algorithms and Applications Richard Szeliski( [book website](http://szeliski.org/Book/))
- Image Processing, Analysis, and Machine Vision,Milan Sonka The University of Iowa, Iowa City, Fourth Edition
- [OpenCv Document](https://docs.opencv.org/4.x/d2/d96/tutorial_py_table_of_contents_imgproc.html)

#### Useful link:
- [Fourier Transform](https://docs.opencv.org/3.4/de/dbc/tutorial_py_fourier_transform.html)
- [Fourier Transformation in Image Processing](https://medium.com/crossml/fourier-transformation-in-image-processing-84142263d734)






