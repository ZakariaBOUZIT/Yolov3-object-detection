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
