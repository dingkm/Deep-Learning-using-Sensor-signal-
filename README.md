##Background

Research content when I was in internship in TOSHIBA R&D Center.

The theme is Performance analysis on sensor-integration based HAR learning model

Human activity recognition, or **HAR**, is a challenging time series classification task. It involves predicting the movement of a person based on sensor data and involves deep domain expertise and methods from signal processing to correctly engineer features from the raw data in order to fit a machine learning model.

Recently, **deep learning methods** such as convolutional neural networks and recurrent neural networks have shown capable and even achieve state-of-the-art results by automatically learning features from the raw sensor data.

This time, the dataset I used is **Heterogeneity Activity Recognition Data Set** from UCI. Here is some description about the dataset. You can see more [here.](https://archive.ics.uci.edu/ml/datasets/Heterogeneity+Activity+Recognition)

>>The dataset contains the readings of two motion sensors commonly found in smartphones. Reading was recorded while users executed activities scripted in no specific order carrying smartwatches and smartphones.

>Activities: ‘Biking’, ‘Sitting’, ‘Standing’, ‘Walking’, ‘Stair Up’ and ‘Stair down’.
>Sensors: Sensors: Two embedded sensors, i.e., Accelerometer and Gyroscope, sampled at the highest frequency the respective device allows.
>Devices: 4 smartwatches (2 LG watches, 2 Samsung Galaxy Gears)
>8 smartphones (2 Samsung Galaxy S3 mini, 2 Samsung Galaxy S3, 2 LG Nexus 4, 2 Samsung Galaxy S+)
>Recordings: 9 users
## Objection
- Time series data in deep neural network with/without temporal layers(LSTM).
- Which is better input data, raw data or frequency domain data? 

##Reimplement two models 
Two published models, one is called [DeepConvLSTM](https://www.mdpi.com/1424-8220/16/1/115/htm)
 and the other is called [DeepSense](https://arxiv.org/abs/1611.01942). You can check the paper.
Model architecture is as followed.
![DeepConvLSTM](https://upload-images.jianshu.io/upload_images/21422961-ae1607efe20b47be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![DeepSense](https://upload-images.jianshu.io/upload_images/21422961-a397f6691cc810c6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
To make baseline comparison, I used two layers of LSTM and also BiLSTM(biodirection LSTM layers).
##Results 
![Comparsion in two datasets](https://upload-images.jianshu.io/upload_images/21422961-3c0f1a4ee24520e8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![CM in two datasets](https://upload-images.jianshu.io/upload_images/21422961-05d0c3b26cfd07fa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
+ Obviously better accuracy in frequency data.
+ Better accuracy in a category-balanced dataset.






