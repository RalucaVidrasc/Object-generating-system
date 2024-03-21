For training and evaluation I used the Detectron2 framework(https://github.com/facebookresearch/detectron2) and the Resnet-50 model. The metrics I focused on were AP and AP50. I chose to use 3 different learning rates to observe the behavior of the model in each of the situations and captured the differences between the 3 methods in order to observe which one has the highest efficiency.

I have therefore analysed the average precision of the model by taking various cases of the training database (with 30%, 50% and 80% more instances than the initial number) , using each of the 3 methods. In addition, we also wanted to see if adding the original set of images to the new, augmented images and then training the model with the merged set makes a significant contribution to the final accuracy. It turned out that using the augmented set is sufficient to achieve good accuracy. Adding the original base can in many cases even harm the final performance, as the model ends up being over-trained. 
Here are some of the results: 

1.  The evaluation of the model trained on the "Simple-Copy-Paste"-augmented dataset:
In these experiments I used the following colours:
* light green -- 30% * dark green -- 30% + train
* pink -- 50%  * red -- 50% + train
* light blue -- 80% * dark blue 80% + train
- learning rate = 0.0001:
  ![AP_0001_scp](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/4b97f70b-812a-4b02-806b-ebbebcb3e015)
- learning  rate = 0.0005:
  ![AP_0005_scp](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/57a10a69-40fc-476a-ad18-04cdeefcafc2)
- learning rate = 0.001:
  ![AP_001_scp](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/b5e8e25a-7d53-431e-a545-c06c8bcfbada)
