
## Definitions of Train, Validation, and Test Datasets
The following provides unambiguous definitions of the three terms.
- Training Dataset: The sample of data used to fit the model.
- Validation Dataset: The sample of data used to provide an unbiased evaluation of a model fit on the training dataset while tuning model hyperparameters.
- Test Dataset: The sample of data used to provide an unbiased evaluation of a final model fit on the training dataset.
We make this concrete with a pseudocode sketch.
```
# split data
data = ...
train, validation, test = split(data)

# tune model hyperparameters
parameters = ...
for params in parameters:
	model = fit(train, params)
	skill = evaluate(model, validation)

# evaluate final model for comparison with other models
model = fit(train)
skill = evaluate(model, test)
```
## Use the k-fold cross-validation
Cross-validation is a resampling procedure used to evaluate machine learning models on a limited dataset. The procedure has a single parameter called $k$ that refers to the number of groups that a given dataset is to be split into. As such, the procedure is oftern called $k$-fold cross-validation.
We can make it concrete with the pseudocode as follows:
```
# split data
data = ...
train, test = split(data)

# tune model hyperparameters
parameters = ...
k = ...
for params in parameters:
	skills = list()
	for i in k:
		fold_train, fold_val = cv_split(i, k, train)
		model = fit(fold_train, params)
		skill_estimate = evaluate(model, fold_val)
		skills.append(skill_estimate)
	skill = summarize(skills)

# evaluate final model for comparison with other models
model = fit(train)
skill = evaluate(model, test)
```

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
Its parameter "dilation rate" defines a spacing between the values in a kernel. A 3x3 kernel with a dilation rate of 2 will have the same field of view as a 5x5 kernel, while only using 9 parameters. Imagine taking a 5x5 kernel and deleting every second column and row. It's as follows.
<figure>
  <img src="https://miro.medium.com/max/474/1*SVkgHoFoiMZkjy54zM_SUw.gif"  width="300" alt=".." title="Optional title" />
  <figcaption>2D convolution using a 3 kernel with a dilation rate of 2 and no padding</figcaption>
</figure>
This delivers a wider field of view at the same computational cost. Dilated convolutions are particularly popular in the field of real-time segmentation. Use them if you need a wide field of view and cannot afford multiple convolutions or larger kernels.

### Transposed Convolutions







