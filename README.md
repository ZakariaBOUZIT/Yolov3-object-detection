# Yolov3-object-detection
You only look once (YOLO) is a state-of-the-art, real-time object detection system.
On a Pascal Titan X it processes images at 30 FPS and has a mAP of 57.9% on COCO test-dev.
>How It Works
Prior detection systems repurpose classifiers or localizers to perform detection. They apply the model to an image at multiple locations and scales. High scoring regions of the image are considered detections.

We use a totally different approach. We apply a single neural network to the full image. This network divides the image into regions and predicts bounding boxes and probabilities for each region. These bounding boxes are weighted by the predicted probabilities.
