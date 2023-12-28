# GAN-based model for generating steel surface defective images
This repository contains my thesis work. It aims at developing a GAN based model for generating defective images to use to improve the accuracy of a classifier to be used as anomaly detection. Our work is carried out in the steelwork area.

## MODEL
Our solution is based on the swapping autoencoder model which is in turns based on the disentangled learning. Indeed, we decompose the input image into two encodings, one representing the defect and one representing the backgrournd. In this way we could transfer the defect from one material to a different one. The material is indentified by having different texture, thus different background.
Moreover, we employed a versatile classifier and a multi-task discriminator on top of the swapping autoencoder.

![](https://github.com/95gas/Defect-transfer-GAN/blob/main/Architecture.png)

## RESULTs
From our results, we could see that our model can in some cases transfer the defect with high-fidelity to the corresponding reference input image and regenerate the texture input image very well. However, in other cases, our model fails and either it generates only a shadow of the defect or apply only the style of the background reference image forgetting the texture details.
This might be due to the disentangled strategy. Indeed one of its drawbacks is that the model might sometimes confuse to distinguish the defect and the texture, which results in the encoding of some piece of information related to the defect into the texture code or viceversa.

Regarding the classifier instead, we could improve the error rate, which decreased from almost 9% to about 5%. This proved that transferring only the style of the material in terms of colour shadings and not the whole tecture details is enough to get a classifier with good accuracy. The first plot displays the accuracy for the augmented dataset, while the second is about the no-augmented data.

![](https://github.com/95gas/Defect-transfer-GAN/blob/main/Classifier/Results/resnet50_Aug_accuracy.png)

![](https://github.com/95gas/Defect-transfer-GAN/blob/main/Classifier/Results/resnet50_NoAug_acccuracy.png)
