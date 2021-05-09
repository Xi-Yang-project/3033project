# Multi-Task Learning Based Age Detection for Image

## Abstract
In  this  work,  we  explore  ways  to  accurately predict  the  age  of  a  person  from  their  portraits.  We regard it as a classification problem first since the target age is divided into severalgroups.  We also explore the possibility of regarding  this  problem  as  regression  as  we  increase the granularity.  After building the age detection model with just one label, two more labels  (gender,  race)  are  added  to  build  the multi-task learning model.  Multitask learningis believed to provide more information for the target task than the single-task leaning model.We learn all three tasks jointly to improve prediction accuracy.  We used both single source and multiple source dataset to examine the possibility of multi-source multi-task leaning.

## Libraries
- cv2
- keras
- efficientnet.keras
- mtcnn 
- numpy
- pandas



## Datasets
In this project, we use two datasets. one is [the IMDB-WIKI dataset](https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/) and the other is [the UTKFace dataset](https://susanqq.github.io/UTKFace/). 
#### IMDB-WIKI dataset
- load_data_imdb.ipynb : load IMDB-WIKI dataset

This dataset contains the most popular 100,000 actors as listed on the IMDb website and (automatically) and their profiles date of birth, name, gender and all images related to that person. There all total 101 age classes.In this project, we only consider the age below 80 and we group those image into 3 age classes, 5 age classes, and 10 age classes.\
For this project, we only use cropped faces(total 171318 images) and ramdom select 20,000 images for training and validatoin. Train-valisation split is implemented in the model code.\
1.download the cropped images and the metadata\
2.run load_data_imdb.ipynb to get the matrix representation for each image.\
2.1 run read_data(db) first to get age and gender information for each image\
2.2 run create_data_3(),create_data_5(),create_data_10() to get images grouped in 3 age classes, 5 age classes, and 10 age classes.
#### UTKFace dataset
-load_data_utkface.ipynb : load UTKFace dataset

This dataset is a large-scale face dataset with long age span (range from 0 to 116 years old). The dataset consists of over 20,000 face images with annotations of age, gender, and ethnicity. This dataset doesn't have metadata file. The labels are included in the file name, like age_gender_race_date&time.jpg. In this project, we only consider the age below 80 and we group those image into 3 age classes, 5 age classes, and 10 age classes.\

For this project, we only use cropped faces(total 21318 images) and ramdom select 20,000 images for training and validatoin. Train-valisation split is implemented in the model code.\
1. download the cropped images
2. run load_data_imdb.ipynb to get the matrix representation for each image.
2.1 run create_3utk_data(),create_5utk_data(),create_10utk_data() to get images grouped in 3 age classes, 5 age classes, and 10 age classes.

## Models
There are 5 files in this models folder. 
- age_prediction.ipynb : model for age prediction based on two datasets
- age_gender_utk.ipynb : model for age-gender prediction based on UTKFace dataset
- age_gender_imdb.ipynb : model for age-gender prediction based on IMDB-WIKI dataset
- age_gender_race_utk.ipynb：model for age-gender-race prediction based on UTKFace dataset
- age_gender_race_multisource.ipynb：model for age-gender-race prediction based on multi-source dataset
build_age_branch(),build_gender_branch(),build_race_branch() are three functions used for adding more tasks.



## Image Prediction
- age_gender_race_reference.ipynb\
1. upload the image
2. upload the wight of final model
3. use MTCNN to detect the face
4. crop the image
5. predict the iamge
6. add box and label for image










