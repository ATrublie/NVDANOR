# NVDANOR
Night Vision / Day and Night classification / Object recognition

The day/night image dataset consists of 200 RGB color images in two categories: day and night. There are equal numbers of images for each category.

I build a classifier that can accurately label these images as day or night, and also implemented ResNet for object detection in that pictures as well as VGG for training on this model and being able to clasiffy them. This model relies on finding distinguishing features between the two types of images!

Note: All images come from the AMOS dataset (Archive of Many Outdoor Scenes).

Al the code can be found in NVDANOR.ipynb 


Steps:

1) First of all i am going to load the dataset and visualize it
These first few lines of code will load the train folder and its subfolders day/night images and store all of them in a variable, IMAGE_LIST. This list contains the images and their associated label ("day" or "night").


2) Step 2: Preprocess the data input images.
This function takes in a list of image-label pairs and outputs a standardized list of resized images and numerical labels.

Resizing every image to a standard size
Encode the target variables

![image](https://user-images.githubusercontent.com/83951228/164650214-8dc7158e-6d67-4a21-86b7-185bf32268ef.png)

Step 3: Feature Extraction
I need to create a feature that represents the brightness in an image. For that i will be extracting the average brightness using HSV colorspace. Specifically, we'll use the V channel (a measure of brightness), add up the pixel values in the V channel, then divide that sum by the area of the image to get the average Value of the image.


![image](https://user-images.githubusercontent.com/83951228/164650257-5958a5c6-bf5c-4497-8de4-906194a0675e.png)




Step 4: Building the classifier
Now we can us that average brightness feature and turn it into a classifier that takes in a standardized image and returns a predicted_label for that image. This estimate_label function should return a value: 0 or 1 (night or day, respectively).



Step 5: We need to Evaluate our Classifier and Optimize it if possible
Here is where we test our classification algorithm using our test set of data that we set aside at the beginning. Below, we load in the test dataset, standardize it using the standardize function we defined above, and then shuffle it. (Shuffling ensures that order will not play a role in testing accuracy).





Lastly we test our model with algorithms such as ResNet-50 model in Keras and VGG to provide object recognition on our images.



Conclusion
With my model i achieved an accuracy of 93.75% by using only one feature extraction, i.e the average brightness of the image. I could work more on this, for example features that involve Hue (a gradation or variety of a color spectrum) and Saturation channels could be extracted for more features which may resault in more accuracy. I also could make more epochs training instead of 5 to achieve more accuracy. Last but not least i can also implement more deep learning models to see different results.
