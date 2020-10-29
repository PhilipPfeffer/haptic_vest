# Haptic Vest Computer Vision Project
Herein lies the almighty Haptic Vest project.

# Components
It consists of a few parts:
 - data_pipeline.ipynb: the code to acquire data from COCO with handy functions to deal with their API (DONE)
 - image_preprocessing.ipynb: data preprocessing code (DONE)
 - resnet43_oracle{X}.ipynb: versions of the resnet34 architecture retrained for dataset sizes {X} (DONE)
 - tensorflow_person_model.ipynb: a keras model that has been hand-toggled
 - rounded_model.ipynb: [does not exist yet] a fully connected neural network with handmade gradient descent changes
 - squeeze_net.ipynb: [does not exist yet] a retrained version of SqueezeNet

# Useful links
- COCO Dataset: https://cocodataset.org/#download
- pycoco API: https://github.com/cocodataset/cocoapi/blob/master/PythonAPI/pycocotools/coco.py
- MobileNet Quantisation paper that mentions a bit-shift network!!! https://arxiv.org/pdf/1712.05877.pdf

# Authors
Philip Pfeffer & Raul Dagir

# Classes
Stanford University: CS229, CS230
