# ClothingClassifier
A clothing classifier using pre-trained neural networks

- Dataset - [Clothing Attributes Dataset](http://huizhongchen.github.io/datasets.html#clothingattributedataset)
- VGG16 weights file - [vgg_weights.h5](https://drive.google.com/file/d/0Bz7KyqmuGsilT0J5dmRCM0ROVHc/view?usp=sharing)

## Methodology-
- Extracted the labels from the .mat file. The code currently contains the classifier for the category_GT.mat file
- The categories were- shirt, sweater, outerwear, t-shirt, tank top, suit, dress
- There were some images that were not labelled (they were labelled as NaN). I re-labelled them as none (or 0)
- Created the training and validation set by using train test split ( 10% of the images were used in the validation set)
- Moved the training and validation images into their respective label directories
- I used image data generator to perform data augmentation (generate more images from the existing image set)
- I used a pre-trained VGG16 model to perform the image classification
- I froze the initial layers and added an output block consisting of 3 dense layers (the last dense layer being the number of classes to be predicted)
- During initial runs, the accuracy for the training set was greater than that of the validation set. So I added dropout to 2 of the dense layers, L1 and L2 regularization and added more parameters to ImageDataGenerator to reduce overfitting

Performance after adjusting for overfitting:
![alt_text](https://github.com/suki2691/ClothingClassifier/blob/master/train-val-acc.png 'Model Accuracy')

- The model was achieving 48% accuracy on the training set
- The confusion matrix for the output:
![alt_text](https://github.com/suki2691/ClothingClassifier/blob/master/confusion_matrix.png 'Confusion Matrix')
- The model was able to identify the clothes categories for those images which were labelled as 'none'


This image was labelled as 'none' in the data set, but the model labelled it as 'sweater'-
![alt_text](https://github.com/suki2691/ClothingClassifier/blob/master/000064.jpg)

## Next Steps-
- Try other pre-trained models
- Increase the time for training


 

