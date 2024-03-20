# Object-generating-system

  This project is my thesis for the bachelor's degree, which aims to augment datasets in order to improve the performance of detection and segmentation models. 
  I used COCO dataset, which can be downloaded from https://cocodataset.org/. I focused on increasing the number of instances in a specified category, especially the "person" class. Thus, I used 3 augmentation methods, each described in the corresponding file: 
  
  1) Clasic augmentation methods (the "Rotate_Flip_Shear.ipynb" file)   
     - In this method, augmentation was done using techniques such as shear, flip, rotate on all images in the training set.
     - Here are some examples of the resulting images:
![RotateFlipShear1](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/83588049-43bf-4601-a3be-782cb74c4aee)

![RotateFlipShear2](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/f604c0f0-10f8-42b2-9b4e-6cbfef8eef1c)

  2) Generative Adversarial Network method (the "GAN.ipynb" file)
     - Used after training a StyleGAN2 model, following the steps from: https://github.com/lucidrains/stylegan2-pytorch . As training dataset, I created a new dataset of white images, in which I pasted single instances from the original COCO training dataset(one instance/ image).
     - Here are some of the newly generated people:
![image](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/ce6bf60d-11d0-495f-8fe5-7ffafe867fea)
     - Here are some final images obtained after augmentation:
![image](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/37bb6864-db75-4d6a-a6d5-5f04a320a9bd)

  3) Simple Copy Paste method (the Simple_Copy_Paste.ipynb file)
     - This method was mainly inspired by this article: https://arxiv.org/abs/2012.07177 . The main idea is selecting 2 random images from the dataset and extract the instances from one and copy them to the other after aplying a series of transformations both to the base image and to the new instance(s). The following image represents the main idea and the sequence of processes:
![Simple-Copy-Paste-aug](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/f0c81e26-03a8-4bde-b017-440692dd1703)
    - Here are some resulted images: 
![image](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/51ce5ccb-1600-4156-9ad7-359ea6567f1d)
