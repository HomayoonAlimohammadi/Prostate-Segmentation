# Prostate Segmentation

<h3>This project was done under the supervision of <b>AI-Medic</b> startup.<br/>
In this project I tried segmenting <b>Transition</b> and <b>Peripheral</b> Zones of Prostate.</h3>


- Here is the [Link][medicaldecathlon] to the Dataset. (Task 5, Prostate)

[medicaldecathlon]: http://medicaldecathlon.com/
<br/>

## Dataset Description:
- Consists of 48 MRI 3D Images with ADC and T2 modality
- 32 are shipped with their relative Mask
- Images dimensions are ~ 256 x 256 x 15
- Mask labels are as follows:
  - 0: Background
  - 1: Peripheral
  - 2: Transition

<br/>

## Main Challenges of the Project:
- These to Zones are almost next to each other
- Overal shape of Prostates varies significantly from case to case
- Low number of training data is troublesome specially in 3D Segmentation

<br/>

## 2D Segmentation Workflow:
- Resizing the Images to the same resolution
- Observing the Histogram of masked zones
- Using np.clip based on the histogram
- Transforming masks to 2 separate binary groups
- Using <b>ResNet18 Backbone</b> pretrained on <b>ImageNet</b>
- Calculating the <b>Dice</b> score
- Updating <b>Learning Rate</b> using <b>CosineAnnealingLR</b>
- Normalizing ADC Images before and after clipping
- Implementation of <b>CLAHE</b> and other simillar Contrast enhancement techniques
- Using 5-fold cross validation for model evaluation

<br/>

# Results

## Label 1: 
- Overall Dices Mean = 0.77
- Overall Dices STD = 0.032
- Overall Dices Best = 0.81
- Per-Subject Dices Mean = 0.71
- Per-Subject Dices STD = 0.044
- Per-Subject Dices Best = 0.78

![Sample Email](https://github.com/homayoonalimohammadi/Prostate-Segmentation/Results/blob/main/media/Label-1.jpg?raw=true)


## Label 2: 
- Overall Dices Mean = 0.91
- Overall Dices STD = 0.012
- Overall Dices Best = 0.92
- Per-Subject Dices Mean = 0.86
- Per-Subject Dices STD = 0.023
- Per-Subject Dices Best = 0.90


![Sample Email](https://github.com/homayoonalimohammadi/Prostate-Segmentation/Results/blob/main/media/Label-2.jpg?raw=true)

