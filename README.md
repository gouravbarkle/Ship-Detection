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

![alt text](https://github.com/gouravbarkle/Ship-Detection/blob/main/image%20dimesion%20sample.png)

when we tend to create a deep neural network, the input vector to the neural network will have 1000*1000*3 = 3 million inputs values and if we have not more but just 1000 nodes in the first hidden layer, the numbers of parameters to learn in the first transition itself will be around 3 million * 1000 = 3 Billion and optimizing these much numbers of parameters is not feasible at all and this is just for a small image in the only first transition, hence we need to have a practical model to deal with this problem. This is where CNN comes to solve this issue.

![alt text](https://github.com/gouravbarkle/Ship-Detection/blob/main/DNN.png)

The above diagram represents a deep neural network with taking input as all 3 million pixels values of the image, which further classifiy it into one of the two predefined output class.

# How CNN can help us to learn these much parameters?
Neither CNN nor any other model can be feasible to learn these many parameters, hence the basic fundamental structure of the CNN model is not like the deep neural networks but it works in a bit different way. The CNN follows a hierarchical model which works on building a network, like a funnel, and finally gives out a fully-connected layer where all the neurons are connected and the output is processed.
Every image contains some sort of feature dependencies at the pixel level which plays an important role in processing the image in the desired way and the convolutions operations in the CNN model act as automatic feature extractors from the image. While if we use an algorithm with pixel vector we lose a lot of spatial interaction between pixels, a CNN effectively uses adjacent pixel information to downsample the image first by convolution and then uses a prediction layer at the end.
Since the feature selection is done by CNN itself automatically, the time we need to spend on the feature engineering before is not required with the CNN.when we compare the features we handcrafted with the detected features by CNN, the performance is much better after. Along with the global and local feature covering, CNN also learns a whole new set of features from the image itself.

# Model Architecture 

![alt text](https://github.com/gouravbarkle/Ship-Detection/blob/main/CNN%20Model.png)

# Experimental Use Case
Changes made in the model architecture:
• To build deeper model, conv2D layers increased.
• More numbers of filters used so that more features can be learned from the image.
• Added Dropout( valued as 0.25) for regularization

