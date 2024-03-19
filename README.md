# Object-generating-system

  This project is my thesis for the bachelor's degree, which aims to augment datasets in order to improve the performance of detection and segmentation models. 
  I used COCO dataset, which can be downloaded from "https://cocodataset.org/". I focused on increasing the number of instances in a specified category, especially the "person" class. Thus, I used 3 augmentation methods, each described in the corresponding file: 
  1) Clasic augmentation methods ( the " Rotate_Flip_Shear.ipynb " file)   
     --> In this method, augmentation was done using techniques such as shear, flip, rotate on all images in the training set.
    ![RotateFlipShear1](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/83588049-43bf-4601-a3be-782cb74c4aee)

![RotateFlipShear2](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/f604c0f0-10f8-42b2-9b4e-6cbfef8eef1c)


  3) Generative Adversarial Network method
     --> Used after training a StyleGAN2 model, following the steps from: https://github.com/lucidrains/stylegan2-pytorch . As training dataset, I created a new dataset of white images, in which I pasted instances from the original COCO training dataset.   
  4) Simple Copy Paste method,
     This method was mainly inspired by this article: "https://arxiv.org/abs/2012.07177"
    
    ![Simple-Copy-Paste-aug](https://github.com/RalucaVidrasc/Object-generating-system/assets/105721568/f0c81e26-03a8-4bde-b017-440692dd1703)
