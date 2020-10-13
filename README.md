![BlueSky-AI Logo](https://media.discordapp.net/attachments/733836130277130263/734503177566552114/unknown.png)

# BlueSky-AI
## Inspiration
Our team is composed of individuals from Alberta and California. Wildfires in these regions have burned through thousands of acres of a land each year, blanketing metropolitan areas in thick plumes of smoke, incurring millions of dollars in damages and displacing a countless number of residents. We believe that predicting potential wildfires before they occur will allow for preventative measures to be taken, reducing the negative effects that wildfires have. 

## What it does
BlueSky-AI provides a robust and highly scalable platform that can be easily used by both developers and end users. Our machine learning model is well optimized and small, so it can run on any computer. Clients can easily configure our platform and will enjoy the efficiency of our well-known technologies, including React.JS, Tensorflow, PyTorch, and Google Maps API. Our data is also taken from reliable sources, including the Fire Program Analysis and the National Wildfire Coordinating Group. For more details on BlueSky-AI, you can visit our website.

## How we built it
Using Panda's and SQLite3, we parsed the SQLITE file the dataset was packaged in. We then loaded everything into a dataframe, which allowed us to easily convert all of the data into values that can be interpreted by a machine learning algorithm. We removed many unnecessary columns of information that we deemed would not be usable in a neural network or would not be related with other data.  Firstly we used a normalisation function to compress all of the integer information into a value between 0 and 1, before implementing a k-folds crossvalidation system in order to distribute the data into testing and training, and to prevent overfitting of the data. 

The model itself performs multidimensional regression using a feed-forward sequential algorithm. We initially tried using a convolutional network but it was not able to establish any relationships within the data. The model has five total hidden layers, first starting with a layer to flatten the data preceded by two dense layers of decreasing input size using the rectified linear unit (relu) as an activation function. After a batch normalization layer, the final layer is another dense layer with the smallest input size and which uses a softmax activation function to feed into our output. After training multiple iterations of our model we were able to achieve a validation accuracy of 91% on test data and we saved the model in that state, allowing for predictions to be made quickly using the saved model. 

After this, we needed to define the prediction function which would be used to output two specific pieces of information, the containment date of the fire as well as it’s nominal size in acres. We needed to reverse the normalization of the output data and convert it back into words so that we could easily deploy it. The prediction function calls the saved model so no training is needed, meaning less time is wasted. Since our package size was limited due to our web hosting, we settled on using tensorflow.js as well as flask in order to deploy the saved model. This would interface through our frontend which was built using React.js


Please see our Devpost for more.
https://devpost.com/software/bluesky-ai
