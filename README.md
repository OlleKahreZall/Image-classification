# Classifying CAPTHA images - with and without a convolutional neural network
In this project, I have classified numbers which appear in images with two different classifiers: partly an algorithm I built myself and, partly a custom deisgned shallow convolutional neural network (CNN) using Keras.

The data used are simplified CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) images, which you probably have seen on websites where you have to prove that you are not a robot, where the task is to classify the numbers 0, 1 and 2 in each image. In total, there are 1200 images as training data in this project.

The accuracy of my own algorithm on the data is 99.7%  and with the CNN, the accuracy score on the training and validation iamges is 99.95% and 100%, respectively. The former is, though, faster than the latter; it took 1.2 seconds for my algorithm to finish and 7.4 seconds for the CNN. My algorithm may be a little bit faster, but I would argue that the CNN is more suitable if new images are given to both classifiers. 

## Data preprocessing

Each image is looks almost like the image below (train_0010), but every image is unique. Even though if two images share the same numbers, both can have different noisy patterns in the images and different sizes on the numbers. So the goal is to construct a classifier that is adjusted for all the data.

To be able to classify each image, I have preprocessed the images in the following way:

* An image like train_0010 is received:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/train_0010.png?raw=true" alt="Sublime's custom image"/>
</p>

* The next step is to remove all the noise in the image and binarize it:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/preprocessed_train_0010.png?raw=true" alt="Sublime's custom image"/>
</p>

* After that, find the contours in the image:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/contours_train_0010.png?raw=true" alt="Sublime's custom image"/>
</p>

* Finally, remove all unnecessary contours (in this case it is the object with red color, since its area is too small to be considered a number) and segment the numbers in the image:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/segmentation_train_0010.png?raw=true" alt="Sublime's custom image"/>
</p>

This process is done for evey image in the training dataset. 

## Classification
The process of building my classifier was done by trial and error; a time consuming, but rewarding in this case, procedure. In this case, specific arrays that contain only black or white pixels where used to identify 0, 1 and 2 and find the specific arrays to identify the numbers took some time. In the CNN, however, classifying the numbers was done very easily by only choosing one hidden layer with relu as activation function. Also, it can probably handle new images even better than my algorithm. The machine won again!

The output of both classifiers of train_0010 results in:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/classified_train__0010.png?raw=true" alt="Sublime's custom image"/>
</p>


