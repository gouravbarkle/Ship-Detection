# Significance of the problem
The objective includes the detection of the ship in the ocean by using the satellite image includes the domain like marine security as primary other than traffic
monitoring, illegal cargo movement, oil discharge control and sea pollution monitoring.
To perform this task, traditionally Automated Identification System (AIS) is used, where the radio frequencies are used to broadcast the location of
the ship wirelessly along with the other relevant information. the role of a receiver can be played by another ship with required tools or a land-based system.
The main disadvantage of using this technology is that it can be bypassed very easily if someone wants to do so, in order to detect the ship one needs
to install the transponder which can be disconnected easily and without a transponder, it is not possible to detect the ship at all.

# Dataset Description
The dataset used for this problem is indeed the image dataset that contains the specific area extracted from the Planet satellite imagery. It contains the
two classes of images labelled as ‘ship’ and ‘no ship’, in total 4000 image samples are used as the whole dataset which includes 1000 images with class ‘ship’ and the rest 3000 are from the class ‘no ship’.
Each sample of the dataset is an RGB image with a resolution of 80x80.
The dataset parsed into the model to train is a JSON formatted text file with the values of the attributes as label, scene_ids and location lists.
• label: Two classes valued as 1 for ‘ship’ and 0 for ‘not ship’.
• scene id: The unique identifier of the PlanetScope visual scene the image chip was extracted from.
• longitude_latitude: The longitude and latitude coordinates of the image centre point, with values separated by a single underscore.

# Model Selection
Since our problem falls under the domain of computer vision, the best choice we could have is to build a model using a Convolution Neural Network.
The introduction of CNNs marks a pivotal moment in object detection history, as nearly all modern systems use CNNs in some form or other.
We have chosen to build a ConvNet from scratch instead of picking a pre-trained model so that the learning from the project could be maximized while keeping the model simple to understand.

So why ConvNets but not deep learning model?
To understand this fact, let's have an example where we need to process an RGB image with the dimension 1000 X 1000.
![alt text](https://github.com/gouravbarkle/Ship-Detection/blob/main/DNN.png)

