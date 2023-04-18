# **Facial Expression Recognition Model**

## Overview of Models
### Repeated K-Fold Cross Validation
After an initial and rather basic sequential model was trained on our data as a simple proof of concept, we turned to trying to optimization in an effort to create a more robust model which would boost accuracy and our confidence in its predictive ability.

As a first step, we actually applied a K-Fold Cross Validation to our data, splitting it into 5 k “folds.” This essentially means we split our data into separate sections, in this case 5, where four of the sections would be combined to form the training data set and one would be held back as the test or validation dataset. AKA an 80-20% train test split in our data.

The real strength of this though is that you can actually train your model sequentially on all five variations of the folds, meaning that a different fold is reserved as the test set and the other four become the training set of each respective model. The idea being then to take the mean of your now five trained models to get an overall accuracy score or even just select the best performing one.

This becomes a useful tool when working with a limited data set and seeking to maximize that available data that can be used to train and test a model on. Especially useful for us as we had reduced our initial Kaggle dataset down from seven to only two emotions earlier, cutting the total data from 28000+ to roughly 8000. Ultimately, it also begets a smarter model with less variance error potential when testing its effectiveness. 

We also ran an evaluation on our k-fold to determine what the performance would be if we were to use a logistic regression model. Our dataset hit at a 66% in that case.

### Build, Compile and Train
Moving forward we built, compiled and trained three unique CNN models using varying and multiple layers of conv2d, max pool2d, flatten as well as a variety of filter numbers, kernel sizes and epochs and steps_per_epoch. Ultimately, the models varied from 30k trainable parameters to 3.8 million.  

After running the keras evaluation function on the models against our withheld test set, they also hit at a pretty wide spectrum in terms of success ratios. Clearly though, our best looked to be Model A which came in at just shy of 96% accuracy when evaluated against our held back test sets. 