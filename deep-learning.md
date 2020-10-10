
# Dataset
The dataset for remote sensing with deep learning:
## PatternNet
PatternNet is a large-scale high-resolution remote sensing dataset collected for remote sensing image retrieval. There are 38 classes and each class has 800 images of size 256×256 pixels. The images in PatternNet are collected from Google Earth imagery or via the Google Map API for some US cities. The following table shows the classes and the corresponding spatial resolutions. The figure shows some example images from each class.


[website](https://sites.google.com/view/zhouwx/dataset)

## Others
[website](https://zhangbin0917.github.io/2018/06/12/%E9%81%A5%E6%84%9F%E6%95%B0%E6%8D%AE%E9%9B%86/)


# sourse (tensorflow)

[website](https://github.com/tavgreen/landuse_classification)




## different Types of Convolutions in Deep Learning
### Dilated Convolutions
Its parameter "dilation rate" defines a spacing between the values in a kernel. A 3x3 kernel with a dilation rate of 2 will have the same field of view as a 5x5 kernel, while only using 9 parameters. Imagine taking a 5x5 kernel and deleting every second column and row.

![image](https://miro.medium.com/max/474/1*SVkgHoFoiMZkjy54zM_SUw.gif)

<img src="https://miro.medium.com/max/474/1*SVkgHoFoiMZkjy54zM_SUw.gif" width="23">
2D convolution using a 3 kernel with a dilation rate of 2 and no padding

![image](https://miro.medium.com/max/474/1*Lpn4nag_KRMfGkx1k6bV-g.gif)



