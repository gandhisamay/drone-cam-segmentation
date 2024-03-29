# Semantic Segmenatation
Semantic Segmentation is process to classify each pixel of the image into some class and then in the final image obtained has various classes marked with different colors.


Drone Cam Images from bird view are taken and segmented into 7 different classes. The Kaggle dataset can be downloaded from the this [website](https://www.kaggle.com/bulentsiyah/semantic-drone-dataset)

## Dataset
The dataset contains `400 images` which are of dimensions ` (3,4000,6000)`. Out of which `390 images` have been taken for training and remaining 10 haven been use for testing the model. The dataset contains the following, 
1) Images from the Cam
2) Label Images(RGB type)
3) Colored Masks Images(RGB type)
4) CSV file containing color channels values for RGB images

For training the model within available hardware resources, the images are resized to a size of `(3,256,256)`.

### Classes Segmented

``` 
Label   Title
Num                
0)	others	      
1)	paved-area         	           
2)	vegetation	            	          
3)	water	            	           	           	   
4)      house	             
5)	person 
6)      vehicles
```
For their corresponding RGB colors check `color scheme.csv` file
## Model
The `U-net model` has been implemented using Pytorch with some minor changes for producing best results. A `BatchNorm layer` has been introduced in the model for faster training which was not present in the original model since it was discovered a year earlier before BatchNorm. 

Also, the number of channels have been reduced to curb with memory issues. The number of channels were reduced to `one-fourth` of the optimal values obtained in U-net architecture.
![network architecture](https://i.imgur.com/jeDVpqF.png)

## Loss 
`Dice Loss` function has been used for training the model. The dice loss function along with `one-hot encoding` rather than using `torch.argmax()` function since the argmax function is not differentiable.

<p align="center">
    <img src="https://github.com/gandhisamay/Drone-Cam-Segmentation/blob/main/Images/Loss%20Segmentation.png" alt="Loss graph">
  </a>
</p>

## Result 
<table>
  <tr>
    <td>Camera Image</td>
     <td>Segmented Image</td>
  </tr>
  <tr>
    <td><img src="https://github.com/gandhisamay/Drone-Cam-Segmentation/blob/main/Images/594.jpg" width=512 height=342></td>
    <td><img src="https://github.com/gandhisamay/Drone-Cam-Segmentation/blob/main/Images/Segmented%20Image.png" width=512 height=342></td>
  </tr>
 </table>

### Notes on Memory
Google Colab's Tesla T4 GPU has been used to train the model. The model has been trained for 50 epochs. 

### License
Credit : Just drop a star as a credit if you use any part of the implementation

