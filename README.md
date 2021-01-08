# Classifying CAPTHA images - with and without a convolutional neural network
In this project, the goal was to classifify the numbers 0, 1 and 2 in CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) images. In total, the dataset consists of 1200 images and the dataset itself was given in an image analysis course at Uppsala University. I solved this task with two different classifiers: partly with an algorithm I built myself and, partly with a custom deisgned shallow convolutional neural network (CNN) using the library Keras.

The accuracy of my own algorithm on the data is 99.7% and with the CNN, the accuracy score on the training and validation iamges is 99.95% and 100%, respectively. The former is, though, faster than the latter; it took 1.2 seconds for my algorithm to finish and 7.4 seconds for the CNN. My algorithm may be a little bit faster, but because the CNN will be a more generalizable model than my algorithm. In addition, constructing the algorithm took much longer than designing the CNN...

## Data preprocessing

Each image looks almost like the image below (train_0010), but every image is unique. Even though if two images share the same numbers, both can have different noisy patterns in the images and different sizes on the numbers. So the goal was to construct a classifier that is adjusted for all the data.

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
The process of building my classifier was done by trial and error; a time consuming, but rewarding, procedure. In this case, specific arrays that contain only black or white pixels where used to identify 0, 1 and 2. Searching for the specific arrays to identify the numbers took some time, because of the difficulty of having the model as generalizable as possible.


. In the CNN, however, classifying the numbers was done very easily by only choosing one hidden layer with relu as activation function. Also, it can probably handle new images even better than my algorithm as stated before... 

The machine won again!

The output of both classifiers of train_0010 results in:

<p align="center">
  <img src="https://github.com/OlleKahreZall/Classifying-CAPTHA-images---with-and-without-neural-networks/blob/main/Images/classified_train__0010.png?raw=true" alt="Sublime's custom image"/>
</p>


