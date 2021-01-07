# Classifying CAPTHA images - with and without neural networks
In this project, I have classified numbers which appear in images with two different classifiers: partly an algorithm I built myself and, partly a custom deisgned shallow convolutional neural network (CNN).

The data used are simplified CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) images, which you probably have seen on websites where you have to prove that you are not a robot, where the task is to classify the numbers 0, 1 and 2 in each image. In total, 1200 images are used. 

The accuracy of my own algorithm on the data is 99.7%  and with the CNN, the accuracy score on the training and validation iamges is 99.95% and 100%, respectively. The former is, though, faster than the latter; it took 1.2 seconds for my algorithm to finish and 7.4 seconds for the CNN. My algorithm may be a little bit faster, but I would argue that the CNN is more suitable if new images are given to both classifiers. 

## Data preprocessing

Each image is looks almost like the image below (train_0010), but each of them is unique. Even though if two images share the same numbers, both can have different noisy patterns in the images and sizes on the numbers. So the goal is to construct a classifier that is adjusted for all the data.

To be able to classify each image, I have preprocessed the images in the following way:

* An image like train_0010 is received:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/train_0010.png?raw=true" alt="Sublime's custom image"/>
</p>

* The next step is to remove all the noise in the image and binarize it:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/preprocessed_train-0010.png?raw=true" alt="Sublime's custom image"/>
</p>

* After this, the contours of the image is found: 

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/contours_train-0010.png?raw=true" alt="Sublime's custom image"/>
</p>

As seen in the image above, four different contours are found, while it should be only three. A solution to this is only to include areas of the contours that are larger than a specific threshold. In this case, the red contour is not considered to be a number since its area is to small.

## Classification
Each image is 
