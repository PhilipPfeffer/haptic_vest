# Haptic Vest Computer Vision Project
Herein lies the almighty Haptic Vest project.

# Authors
Philip Pfeffer & Raul Dagir

# Classes
Stanford University: CS229, CS230

# Papers
Stanford CS229: https://github.com/PhilipPfeffer/haptic_vest/blob/main/CS229_Final_Paper.pdf

Stanford CS230: https://github.com/PhilipPfeffer/haptic_vest/blob/main/CS230_Project_Final_Report.pdf

# Description
Imagine being visually impaired but still able to feel the movement of surrounding crowds and cars on your body. Imagine being a peacekeeper but resting assured that unexpected movements behind you will be transduced into your shirt. Imagine being a twenty year-old playing Pokémon Go and receiving a haptic vibration pointing you towards your next catch. This can be achieved by wearing a 'haptic vest' that uses a camera to capture images, a computer vision model to process them and coin-sized vibration motors that vibrate the shirt to communicate the output

## Video Description of MobileNetV1+V2 Methods
Featuring Raul Dagir (GitHub: rgdagir), who helped me with this portion of the project.
Link: https://youtu.be/GM2dVZ0eXgQ

# Project Methods
## Retraining MobileNets (Stanford CS230 - Deep Learning)
This section/paper describes the design of the computer vision model for such a garment. The input to our algorithm is a (128, 128) greyscale image for MobileNetV1 and a (96, 96) greyscale image for MobileNetV2. We then use a retrained publically-available convolutional neural network (CNN) architecture called MobileNet to output a predicted classification of the image. The model classifies the image into the classes ['person', 'car', 'neither']. 

## Creating a new optimiser, Pow2Opt (Stanford CS229 - Machine Learning)
Computer vision models tend to be large and require many matrix multiplications to perform inference on a new image. This poses challenges on consumer edge devices, such as the Arduino Nano BLE Sense and Raspberry Pi 4, where memory and compute are scarce. 

## Proposed Methods
### Pow2Opt on CNN
Apply the Pow2Opt optimiser to a CNN, not just a fully-connected network. I already tried this with a pre-trained MobileNetV2, but it didn't work. However, it should be possible to get this working. 

Pros: This would decrease the number of parameters AND probably increase accuracy compared to the fully-connected network.
Cons: This makes the device-side code more difficult. You have to pack and then unpack the representation. Why not use easier quantisation?

### Two models 
Use two binary classification models, the first classifies ['person', 'neither'] and the second classifies ['car', 'neither']. Each counts as a vote and the system decides what is present given the models. This can also serve for multilabel classification.

Pros: can run these models concurrently on different arduinos AND binary classification should be simpler than three-class.
Cons: have to develop two models AND have to buy several arduinos on each vest.

This can also be expanded to use a third model that classifies ['person', 'car'].


# Components
The components of the project are:
 - data_pipeline.ipynb: the code to acquire data from COCO with handy functions to deal with their API (DONE)
 - image_preprocessing.ipynb: data preprocessing code (DONE)
 - resnet43_oracle{X}.ipynb: versions of the resnet34 architecture retrained for dataset sizes {X} (DONE)
 - tensorflow_person_model.ipynb: a keras model that has been hand-toggled
 - transfer_learning.ipynb: a TF.org example of mobilenet being retrained
 - rounded_model.ipynb: [does not exist yet] a fully connected neural network with handmade gradient descent changes
 - squeeze_net.ipynb: [does not exist yet] a retrained version of SqueezeNet


# Useful links
- COCO Dataset: https://cocodataset.org/#download
- pycoco API: https://github.com/cocodataset/cocoapi/blob/master/PythonAPI/pycocotools/coco.py
- MobileNet Quantisation paper that mentions a bit-shift network!!! https://arxiv.org/pdf/1712.05877.pdf
