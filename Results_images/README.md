For training and evaluation I used the Detectron2 framework(https://github.com/facebookresearch/detectron2) and the Resnet-50 model. The metrics I focused on were AP and AP50. I chose to use 3 different learning rates to observe the behavior of the model in each of the situations and captured the differences between the 3 methods in order to observe which one has the highest efficiency.

I have therefore analysed the average precision of the model by taking various cases of the training database (with 30%, 50% and 80% more instances than the initial number) , using each of the 3 methods. In addition, we also wanted to see if adding the original set of images to the new, augmented images and then training the model with the merged set makes a significant contribution to the final accuracy. It turned out that using the augmented set is sufficient to achieve good accuracy. Adding the original base can in many cases even harm the final performance, as the model ends up being over-trained. 

Here are some of the results: 
In the following images :
bbox - bounding box 
segm - segmentation 
1.  The evaluation of the model trained on the "Simple-Copy-Paste"-augmented dataset:
In this experiment I used the following colours:
* light green -- 30%
* dark green -- 30% + train
* pink -- 50%  
* red -- 50% + train
* light blue -- 80%
* dark blue -- 80% + train
* gray -- original dataset
    - learning rate = 0.0001:
  ![AP_0001_scp](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/4b97f70b-812a-4b02-806b-ebbebcb3e015)
    - learning  rate = 0.0005:
  ![AP_0005_scp](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/57a10a69-40fc-476a-ad18-04cdeefcafc2)
    - learning rate = 0.001:
  ![AP_001_scp](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/b5e8e25a-7d53-431e-a545-c06c8bcfbada)
2. The evaluation of the model trained on the "GAN"-augmented dataset:
  In this experiment I used the following colours:
  * green - 30%
  * light blue - 50%
  * purple - 80%
  * gray - original dataset
    
       Here are the results for the learning rate of 0.0005:
  ![GAN_0005](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/ee449f1f-32a0-442c-8186-b53b1b9748d7)

3. The evaluation of the model trained on the "RotateFlipShear"-augmented dataset:
   
   The applying of this type of augmentation by itself(without the adding of the original dataset) had weaker results than the original database. However, when I trained the model with the merged set I obtained better results than the original dataset:
  In this experiment:
* the original dataset has the following colours, in order: purple, yellow and green
* the augmented dataset has the following colours, in order: pink, green and blue
  
  Here are the results for the learning rate of 0.0005:
![AP_0005_RFS](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/cd329e6a-738e-48dc-b442-0a762a8a4425)

    CONCLUSIONS
- When 30% more instances are added, the density of the objects grows slower than the original set. On the other hand, randomly copying 80% of the instances can lead to a sudden increase in density, which may be due to a large number of overlaps, thus covering important elements of the base image.
- A limitation may be the idea that the base images are sometimes resized at a too low resolution, Detectron2 not being able to extract all the necessary features, and generally having difficulties in recognising small objects.
- If a low learning rate is used, the metrics begin to have small values, after which they steadily increase. As the learning rate increases, the variations results begin to be briefer, reaching convergence more quickly. Regardless of the method used, however, the results of the values eventually stabilise. Thus, all learning rates reach similar performance after a number of epochs, but what differs is the rate of increase and the trajectory.
- The "simple-copy-paste" method does not depend on the locations where the instances are copied (e.g. copying the instances into the images that already contained the object in question, copying into the images that did not correspond to the chosen class and copying the instances into all the images randomly).
- The GAN method depends very much on how the training was done. Thus, ın case ın which the masks of the instances offered for training are uncertain and show various variations not specific to the class ın question, the trained model very easily be confused and may learn inappropriate features.
- The "copy-paste" method obtained significantly better results than the other objects applied, thus highlighting the power of this type of augmentation.

