# Gesture-Dataset
## Original Dataset
### Creation of the dataset
We make a gesture dataset by using mobile phone capture and OpenCV library calling local camera capture. In different scenarios, various methods are used to enhance the diversity of samples, such as different people turning the angle during the shooting process, deforming the fingers, adjusting the distance between the gesture and the local camera, etc. The self-made dataset in this study collected gestures from 54 people, each with 26 gestures. These 26 gestures represent the 26 letters A to Z of American Sign Language (ASL) gestures. There are 106 samples in each category, and a total of 2756 gesture samples.

![image](https://github.com/KayViolet/Gesture-Dataset/blob/main/GestureSample/ASL%20Gesture%20Sample.jpg)
<p align="center">Fig. 1 ASL Gesture Sample Example</p>

### The file structure of the dataset
The original gesture images are placed in the OriginalData folder, which contains the SourceImages folder (.jpg), and the LabelImg annotation folder (.xml). The gesture dataset is divided into training set, validation set and test set according to the ratio of 6:2:2. The divided dataset is placed in the images folder, and its labels are placed in the labels folder.
The file structure is as follows:

     └── OriginalData
         └── Annotations
             └── xxxxxxx.xml
         └── images
             └── train
             └── val
             └── test
         └── labels
             └── train
                 └── xxxxxxx.txt
             └── val
             └── test
         └── SourceImages
             └── xxxxxxx.jpg

## Small Target Dataset
### Creation of the dataset
In order to simulate the distance change between the gesture and the camera and the drastic target ratio, the original dataset is scaled according to the relative pixel ratio, and four gesture samples are randomly selected to form a gesture sample to form a custom small sample gesture dataset.
The specific steps for constructing a small target dataset with large-scale variance are:
  - Randomly select four samples for splicing, and the splicing method adopts diagonal splicing;
  - Extract the pixel values of the height and width of the four gesture samples, according to The extracted relative pixels are scaled, so that the high-pixel samples occupy a larger proportion of the image, and the low-pixel samples occupy a smaller proportion of the image, and determine the pixels of the combined large image;
  - Determine the stitching center point, four samples Select a vertex for splicing, that is, the lower right corner of the upper left sample, the lower left corner of the upper right sample, the upper right corner of the lower left sample, and the upper left corner of the lower right sample; 
  - Create an empty large image, fill each small sample, and construct Small target samples with large scale variance.
![image](https://github.com/KayViolet/Gesture-Dataset/blob/main/GestureSample/Annotation%20example%20of%20small%20target%20gesture%20samples.jpg)
<p align="center">Fig. 2 Annotation example of small target gesture samples</p>
The small target dataset reasonably simulates the drastically changing target ratio. After splicing, there are a total of 11,140 small target gesture samples, including 26 gestures and composed of 54 people.

### The file structure of the dataset
The file structure of the small target dataset is the same as the original dataset. The file structure is as follows:

     └── GestureSmallTarget
         └── Annotations
             └── xxxxxxx.xml
         └── images
             └── train
             └── val
             └── test
         └── labels
             └── train
                 └── xxxxxxx.txt
             └── val
             └── test
         └── SourceImages
             └── xxxxxxx.jpg
