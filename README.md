# Bayes classifier using GMM

## Datasets:
Dataset 1: Nonlinearly separable classes: 2-dimensional data of 2 or 3 classes that are
nonlinearly separable. 

Dataset 2: Real world data set:

    (a) Two-dimensional speech dataset (vowel data) 
    (b) 3 class scene image datasets
    (c) Cervical cytology (cell) image dataset

## Tasks Implemented

1. Classification task: Build the Bayes classifier using GMM on Dataset-1, Dataset-2(a) and, Dataset-2(b)
Parameters of GMM are to be initialized using K-means clustering.

2. Segment the cell images by clustering the local feature vectors from cell
image datasets into 3 groups using (a) K-means clustering and (b) Modified K-
means clustering (using Mahalanobis distance).

## Features Extracted from Images Dataset

Features to be extracted from images of Dataset 2(b) and Dataset 2(c):
1. Features from images of Dataset 2(b):
   
    1. Colour histogram feature:
    
          • Consider 32 x 32 nonoverlapping patches on every images (from training and test sets).
          For example, if image size is 256 x 256, there will be 32 number of 32 x 32
          nonoverlapping patches.
         
          • Extract 8-bin colour histogram from every colour channel (R, G and B) from a patch. It
          results in 3, 8-dimentional feature vectors. Concatenate them to form 24-dimentional
          feature vector.
         
          • Similarly extract 24-dimentional feature vector from every patch.
      
          • Stack the 24-dimentional feature vectors corresponding to every patch in an image and
          save them as a file in the corresponding class folder.
      
          • Thus, an image is represented as set (collection) of 24-dimentional colour histogram
          vectors representation
      
          • Repeat the above steps to all the images in training and test sets of all the classes.
          Colour histogram computed as follows from a colour channel:
          NOTE: Colour histogram is computed at every patch
      
          • When the given image is read, it will be read as 3-dimentioanl matrix of pixel values.
          Each patch of an image is also a 3-dimentioanl matrix of pixel values. Each dimension
          is corresponding to a colour channel. The pixel values in each colour channel are in the
          range 0 to 255.
      
          • For a colour channel,
         
             ◦ Divide this range into 8 equal bins.
      
             ◦ Count the number of pixels falling into each bin. This results in a vector of 8
                values.
         
             ◦ This is the 8-dimentional colour histogram (from a colour channel) feature vector.
      
             ◦ Normalise this vector by dividing it by the number of pixels in that patch.
      
         • Do the same for other colour channels. Concatenate those three 8-dimentional colour
          histogram vectors to form 24-dimentional vector.
   
    2. Bag-of-visual-words (BoVW) feature using K-means clustering:
    
          • Take the 24-dimentional colour histogram feature vectors of all the training examples
          of all the classes.
      
         • Group them into 32 clusters using K-means clustering algorithms.
      
         • Now take an image, assign each 24-dimentional colour histogram feature vector to a
          cluster.
      
         • Count the number of feature vectors assigned to each of the 32 clusters.
      
          • This results in a 32-dimentional BoVW representation for that image.
      
          • Normalise this vector by dividing it by the number of 24-dimentional histogram feature
          vectors in that image.
      
          • Repeat this for every image in training and test set.

2. Features from images of Dataset 2(c):

    • Consider 7 x 7 overlapping patches with a shift of 1 pixel on every training cell images.
    
    • Compute mean and standard deviation of intensities of pixels in the 7 x 7 patch.
    
    • Thus a 7 x 7 patch is represented as 2-dimentional feature vector.
    
    • In the similar way compute 2-dimentional feature vector from every patch from every
    training image.
    • Stack all the 2-dimentional feature vectors in a file.
