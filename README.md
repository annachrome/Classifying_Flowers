# Summary

Fine-tuned ResNet-50 on augmented Flowers-102 Dataset.
Validation Accuracy: 98.86%

<img width="641" alt="Screenshot 2023-11-27 at 10 50 53 AM" src="https://github.com/annachrome/Classifying_Flowers/assets/84694222/85588948-2284-4bef-ba04-224d5db1dbbc">

# Exploratory Data Analysis (EDA)
The number of images per label has a mean of 80.284 and standard deviation of 44.277.

Since the class sizes' standard deviation is very high relative to the mean, we must undersample large classes to reduce class imbalance.

<img width="640" alt="Screenshot 2023-11-27 at 10 52 29 AM" src="https://github.com/annachrome/Classifying_Flowers/assets/84694222/36ed9225-f5ba-4764-a575-f62f34d21d63">

And since image dimensions vary greatly, resizing all images to a fixed size, e.g. (224, 224), may cause an image with (WLOG) width < height to lose a disproportionate amount of information along the height axis.

Hence, dynamically resize and pad the images to maintain their original aspect ratios.

# Model
ResNet-50 pre-trained on ImageNet. 

According to Wightman (2021), _ResNet Strikes Back_, while ResNet is a pretty basic model far from SOTA, with the right combination of data augmentations, fine-tuning and hyperparameters, the model can yield incredibly high accuracy on its own. This is an incredibly valuable finding for engineers with limited compute resources.

# Evaluation
<img width="442" alt="Screenshot 2023-11-27 at 11 04 03 AM" src="https://github.com/annachrome/Classifying_Flowers/assets/84694222/b7aed43f-f27a-4481-bacb-99a3377f50dd">
In version 4.0, accuracy was 93% so I added CutMix augmentation as Wightman suggested (and altered the criterion accordingly). 

<img width="1205" alt="Screenshot 2023-11-27 at 9 11 28 AM" src="https://github.com/annachrome/Classifying_Flowers/assets/84694222/708a3bf1-ad97-4480-b785-9fb9b9a021ad">

In version 5.0, accuracy was 97%. Misclassified images were often wrongly labeled according to color. Hence, I added augementations grayscaling and color jitter, which upped accuracy to the current 98.86%.



