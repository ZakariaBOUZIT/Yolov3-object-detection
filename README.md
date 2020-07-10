# Yolov3-object-detection
You only look once (YOLO) is a state-of-the-art, real-time object detection system.

>How It Works

Prior detection systems repurpose classifiers or localizers to perform detection. They apply the model to an image at multiple locations and scales. High scoring regions of the image are considered detections.

We use a totally different approach. We apply a single neural network to the full image. This network divides the image into regions and predicts bounding boxes and probabilities for each region. These bounding boxes are weighted by the predicted probabilities.

>What i have done ?

Yolo has gained a lot of popularity over the years since it is a real time detection method. This means that not only we will be able to classify an object but we will also locate it and extract the bounding box enclosing that object.

This is one of the easiest method since it does not require an installations other than opencv. We will use the configuration and weights files provided by the author on the darknet website.
______________________________________________________________________________________________________________________________________________________________________________
# Read Coco Names

The next step is to load the yolo3 model. Since it was trained on the coco dateset we will first collect the names of our classes. This can be imported from the coco.names file. You can find this file in the downloads section of the post. Another way of doing this would be to just create a list and manually type all the class names. Since we have 80 different classes its better to use the file instead.

![](https://raw.githubusercontent.com/zackq88/Yolov3-object-detection/master/Capture.PNG)

# Load the model files

Any model has two main components. One is the Architecture and the other is weights. For yolo3 we have separate files for both. So we will import the configuration file that has the architecture and the weights file that contains the weights.

On the Yolo website we can find different cfg and weight files. You try these and see which fits your needs the best. In my opinion 320 is the best trade off between speed and accuracy.

we can load our model using the readNetFromDarkNet function. We will also set the backend to openCV and the target to CPU. I did try the GPU as well but it did not work for me.

# Input Image to Network

We cannot send our image form the camera directly to the network. It has to be in a certain format called blob. We can use the blobFromImage function which creates 4-dimensional blob from image. Optionally resizes and crops image from center, subtract mean values, scales values by scalefactor, swap Blue and Red channels. We will keep all the values at default.

Now based on which image size we used when we downloaded the cfg and weight files, we will set the size of the image. Since we used 320 we will set our whT (widthHeightTarget) parameter to 320.

# Get Output of Network
Since the Yolo3 Architecture has 3 output layers we have to find their names so we can get their outputs.

![](https://raw.githubusercontent.com/zackq88/Yolov3-object-detection/master/yolo%203%20structure.jpg)

To get the names we can use the getLayerNames fucnction. This returns all the names, but what we need are the names of only the output layers. So we can use the getUnconnectedOutLayers function which returns the indices of the output layers. Now we can simply use these indices to find the names from our layersNames list. Since we use 0 as the first element we have to subtract 1 from the indices we get form the getUnconnectedOutLayers function.

This will return us a list of 3 arrays of the following size

300 x 85

1200 x 85

4800 x 85

