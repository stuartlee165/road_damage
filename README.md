# Road Damage Model Identifier Training and Implementation
## An Image Segmentation Project Using FastAi

This was a project to create a CNN model which can identify road damage from uploaded images. I used the FastAi library and trained a unet_learner with a ResNet50 architecture. The project included sourcing image data, manually labelling 100 images, model training and implementation. 

## Data Collection
Initially I scraped images of 'damaged roads' from duckduckgo, however the range of images found was very broad. I wanted to focus on car dash-cam style photos only and found a pre compiled dataset RDD2020 which comprises 26,336 road images from India, Japan, and the Czech Republic with more than 31,000 instances of road damage. The dataset captures four types of road damage: longitudinal cracks, transverse cracks, alligator cracks, and potholes. While the dataset includes labeling data I wanted to create my own labels in order to run the process from scratch. Further, the labels included in the dataset are rectangular where as the method I employed uses polygons. 

Labelling the data I used the following programmes:

<a href="https://github.com/wkentaro/labelme" target="_blank"> Labelme</a>
<a href="https://github.com/fcakyon/labelme2coco" target="_blank"> Labelem2coco</a>

<p align="center">
  <img src="https://github.com/stuartlee165/car_damage_classifier/blob/main/images/carapp.png" width="400"/>
</p>




### Web App Output


<a href="https://course.fast.ai/" target="_blank"> This mini project was completed as part of the FastAi course.</a>
