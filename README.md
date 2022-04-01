# Fruit-Ripeness-Detection
This project aims to classify 6 types of fruit (apple, banana, orange, pomegranate, mango and papaya) into 3 classes of raw, ripe or rotten

## Data Collection
The model was trained on the dataset that was scraped from Google Images using selenium.

I designed a programme that searches for photos on a webpage. The img tag will be used to identify the photos, and the CSS selector Q4LuWd will be applied to each image.  It saves the image source to a list after it has been found. This pattern repeats itself until the required number of images is found. If the required number of photographs is not met, I have included a backup option in the software. 

The list of image urls is then sent to a different function that saves the image to the folder of its class

Our model will train on the following set of 18 total classes 

![Screenshot (107)](https://user-images.githubusercontent.com/62397380/161302893-86afb3eb-1f35-4c9f-85cb-77820d3144b5.png)


Each class has around 110 images to it(following is an example of what the ripe apple class folder contains)

![Screenshot (108)](https://user-images.githubusercontent.com/62397380/161303088-9a0512a0-2545-4db8-9a5f-f4ed02678cd1.png)

## Model Building and Training
I used transfer learning to import the MobileNetv2 model containing weights trained on imagenet dataset. To this base layer of MobileNetV2, we add our global spatial average pooling layer, a fully connected layer and a logistic layer at the end. I used ReLu activation function in all the layers except the last one which is the logistic layer, for which i used a the sigmoid activation function.

The model was trained for 5 epochs in two stages and this was the graph obtained:

![Picture1](https://user-images.githubusercontent.com/62397380/161310069-05783a93-5985-4781-9723-c8351dab3f4c.jpg)

Our model returned the following result:

![Fruit Ripeness](https://user-images.githubusercontent.com/62397380/161310731-2eb88126-5403-4647-8f1d-aebe52b2f220.jpg)

## Deployment
The model was then deployed on raspberry pi 4. The raspbian os does not support tensorflow 2, hence I had to convert the keras model into tensorflow's frozen graph model so that I can read the model using OpenCV's DNN module. I achieved this with the help of [this](https://ksingh7.medium.com/part-iii-convert-keras-model-to-tensorflow-frozen-graph-model-a6aa6b1aaeee) blog post.

