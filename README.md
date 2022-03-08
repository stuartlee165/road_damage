# Road Damage Model Identifier Training and Implementation
## An Image Segmentation Project Using FastAi

This was a project to create a CNN model which can identify road damage from uploaded images. I used the FastAi library and trained a unet_learner with a ResNet50 architecture. The project included sourcing image data, manually labelling 100 images, model training and implementation. 

## Data Collection
Initially I scraped images of 'damaged roads' from duckduckgo, however the range of images found was very broad. I wanted to focus on car dash-cam style photos and found a pre compiled dataset <a href="https://www.sciencedirect.com/science/article/pii/S2352340921004170" target="_blank"> RDD2020</a> which comprises 26,336 road images from India, Japan, and the Czech Republic with more than 31,000 instances of road damage. The dataset captures four types of road damage: longitudinal cracks, transverse cracks, alligator cracks, and potholes. While the dataset includes labelling data I wanted to create my own labels in order to run the process from scratch. Further, the labels included in the dataset are rectangular whereas the method I employed uses polygons. As a starting point I took a sample of 100 images. 




Labelling the data I used the following programmes:

<a href="https://github.com/wkentaro/labelme" target="_blank"> Labelme</a>
<a href="https://github.com/fcakyon/labelme2coco" target="_blank"> Labelem2coco</a>

Using label me I manually annotated 100 images with the areas of road that had some sort of damage. Each image could include multiple polygons. At this stage I used one label only 'damage' although it would be possible to add multiple categories of label (e.g. include information on damage severity). Label me creates Coco files which maps the labels created to the images. 

<p align="center">
  <img src="https://github.com/stuartlee165/road_damage/blob/main/notebooks/images/labelme.jpg" width="400"/>
</p>

The next step was to create an annotations.json file which summarises in one file each of the json files for each image in the data set. This is then used to create masks (png format) for each image.


### Model Training and Implementation
A model was trained using the FastAi library in Paperspace. The process followed the standard format for training a model with FastAi. Create a datablock (the difficult part here is creating the functions which will process the image and mask (label) data). Create a dataloader, then create a unet_learner object (which is a modified form of a cnn_learner specific for image segmentation tasks). Resnet50 architecture was utilised. Then fit the model (fine_tune as we are using predefined weights for Resnet architecture). 

Some examples from the training data:
<p align="center">
  <img src="https://github.com/stuartlee165/road_damage/blob/main/notebooks/images/mask.png" width="400"/>
</p>

Not withstanding the fact that the dataset at this stage contains only 100 images, applying the model to unseen data showed surprisingly good results. 

<p align="center">
  <img src="https://github.com/stuartlee165/road_damage/blob/main/notebooks/images/test.png" width="400"/>
</p>



