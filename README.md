# Semantic Segmentation
## Michael DeFilippo

#### Please see my [project code](https://github.com/mikedef/CarND-Semantic-Segmentation) for any questions regarding implementation.
---

# Overview
This repository contains all the code needed to complete the Semantic Segmentation project. The main goal of the project is to label the pixels of a road in images using a Fully Convolutional Network (FCN). The Kitti Road dataset was used for the training data. 

A FCN was used for semantic scene segmentation because it retains the spatial information during training. This is helpful to identify objects in an image. The architecture used in the project was composed of three parts.
 - Encoder: This was the pretrained VGG16 neural network
 - 1X1 convolution
 - Decoder: Transposed convolutions and skip connections
 
 # Model Output
 Below are a random sample of the original test images and the output of the network at various training epochs.
 ### Original Images:
 Random sample of the original training images
 ![alt text](/images/um_000000.png)
 ![alt text](/images/uu_000095.png)
 
 ## Model Output at 6 Epochs:
 ![alt text](/images/um_000000-6epoch.png)
 ![alt text](/images/uu_000095-6epoch.png)
 
  ## Model Output at 12 Epochs:
 ![alt text](/images/um_000000-12epoch.png)
 ![alt text](/images/uu_000095-12epoch.png)
 
  ## Model Output at 24 Epochs:
 ![alt text](/images/um_000000-24epoch.png)
 ![alt text](/images/uu_000095-24epoch.png)
 
  ## Model Output at 48 Epochs:
 ![alt text](/images/um_000000-48epoch.png)
 ![alt text](/images/uu_000095-48epoch.png)

The models starts to correctly identify road pixels fairly well as training goes up. 

## Original Readme: 
# Semantic Segmentation
### Introduction
In this project, you'll label the pixels of a road in images using a Fully Convolutional Network (FCN).

### Setup
##### GPU
`main.py` will check to make sure you are using GPU - if you don't have a GPU on your system, you can use AWS or another cloud computing platform.
##### Frameworks and Packages
Make sure you have the following is installed:
 - [Python 3](https://www.python.org/)
 - [TensorFlow](https://www.tensorflow.org/)
 - [NumPy](http://www.numpy.org/)
 - [SciPy](https://www.scipy.org/)
##### Dataset
Download the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) from [here](http://www.cvlibs.net/download.php?file=data_road.zip).  Extract the dataset in the `data` folder.  This will create the folder `data_road` with all the training a test images.

### Start
##### Implement
Implement the code in the `main.py` module indicated by the "TODO" comments.
The comments indicated with "OPTIONAL" tag are not required to complete.
##### Run
Run the following command to run the project:
```
python main.py
```
**Note** If running this in Jupyter Notebook system messages, such as those regarding test status, may appear in the terminal rather than the notebook.

### Submission
1. Ensure you've passed all the unit tests.
2. Ensure you pass all points on [the rubric](https://review.udacity.com/#!/rubrics/989/view).
3. Submit the following in a zip file.
 - `helper.py`
 - `main.py`
 - `project_tests.py`
 - Newest inference images from `runs` folder  (**all images from the most recent run**)
 
 ### Tips
- The link for the frozen `VGG16` model is hardcoded into `helper.py`.  The model can be found [here](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/vgg.zip)
- The model is not vanilla `VGG16`, but a fully convolutional version, which already contains the 1x1 convolutions to replace the fully connected layers. Please see this [forum post](https://discussions.udacity.com/t/here-is-some-advice-and-clarifications-about-the-semantic-segmentation-project/403100/8?u=subodh.malgonde) for more information.  A summary of additional points, follow. 
- The original FCN-8s was trained in stages. The authors later uploaded a version that was trained all at once to their GitHub repo.  The version in the GitHub repo has one important difference: The outputs of pooling layers 3 and 4 are scaled before they are fed into the 1x1 convolutions.  As a result, some students have found that the model learns much better with the scaling layers included. The model may not converge substantially faster, but may reach a higher IoU and accuracy. 
- When adding l2-regularization, setting a regularizer in the arguments of the `tf.layers` is not enough. Regularization loss terms must be manually added to your loss function. otherwise regularization is not implemented.
 
### Using GitHub and Creating Effective READMEs
If you are unfamiliar with GitHub , Udacity has a brief [GitHub tutorial](http://blog.udacity.com/2015/06/a-beginners-git-github-tutorial.html) to get you started. Udacity also provides a more detailed free [course on git and GitHub](https://www.udacity.com/course/how-to-use-git-and-github--ud775).

To learn about REAMDE files and Markdown, Udacity provides a free [course on READMEs](https://www.udacity.com/courses/ud777), as well. 

GitHub also provides a [tutorial](https://guides.github.com/features/mastering-markdown/) about creating Markdown files.
