
## Project 1: Build a tag inspection system for a fulfillment center.                                                                         

Background: A fulfillment center acts as a pseudo-warehouse for many OEMs
and ships parts based on purchase orders (PO) from its customers. build an optical
verification system for their outbound parts, i.e. if the parts being shipped are
as per the PO or not.
### instructions to Run the code for Assignment 1 (inspection system)


 - [Py file containing main codes](https://github.com/ravipratap366/PhotoGAUGE_assignment1-2/blob/main/inspection_system.py)
 - [requirements.txt](https://github.com/ravipratap366/PhotoGAUGE_assignment1-2/blob/main/requirements.txt)
 - [data]
 - [Jupyter notebook (contains other approaches i tried)](https://github.com/ravipratap366/PhotoGAUGE_assignment1-2/blob/main/INSPECTION%20SYSTEM.ipynb)
 - [pdf file (contains steps i tried in this project)](https://github.com/ravipratap366/PhotoGAUGE_assignment1-2/blob/main/PhotoGAUGE_final.pdf)






## summary 
#### approch 1
In the project inspection system ,I tried with 2 approaches
approache 1 -Frist I select this image containing purches order
and pick sheet. 
Then , i extract all purchase orders items by cv2..perform operation like
(Load image, grayscale, median blur, sharpen image, Threshold,erode ,dilate
and morph close)
after performing these operation ,i tried to find contours 
and filter using threshold area.(min_area = 50000 max_area = 110000),
after that i rotate the extracted image image to perform OCR.
after performing OCR by easyocr , i get the item number.
then i make list of item from pick sheet to validate it with extracted item.



#### approch 2 
I also tried with pyzbar to read barcode from image.pyzbar read the barcode 
from extracted image.then i validate with picksheet.in this approch i face 
a problem in reading few bar code (might be improve).

#### I explained the steps in the documentation.








# -----------------------------------------





## Project #2: Build an optical system for measuring length of pipes

Background: Calculate the length of pipe in a lot captured by drone .
Individual joints , which are 40’-50’ long, are
threaded together to form a continuous pipe that is inserted into 
a drill hole.these joints are stored in an intermediate station. 
When a customer requests a certain length of pipe, the
joints are brought out from storage and laid out in a single layer on 
stands , measured by capturing image from drone camera.
 A group may contain anywhere from 20 to 300 pipes.





### instructions to Run the code for Assignment 2 (pipe lenth measure)


 - [colab link containing main codes(colab link)](https://colab.research.google.com/drive/1EwUTqSNqAwppkjmCQctQ6qWR6nHO6YnP#scrollTo=BC90wcMqwnt-)
 - [Required Data(google drive link) ](https://drive.google.com/drive/folders/1-M64d6-cWzQgiG7vxSfu-QN3EdBYw9PT?usp=sharing)
 - [Jupyter notebook (contains other approaches i tried)](https://github.com/ravipratap366/PhotoGAUGE_assignment1-2/blob/main/pipe_len_Detectron2_final_(2).ipynb)
 - [pdf file (contains steps i tried in this project)](https://github.com/ravipratap366/PhotoGAUGE_assignment1-2/blob/main/PhotoGAUGE_final.pdf)







## summary
In this problem statement ,i train detectron2,Detectron2 is Facebook\
AI Research's next generation library that provides state-of-the-art
detection and segmentation algorithms. It is the successor of 
Detectron and maskrcnn-benchmark. It supports a number of computer
vision research projects and production applications in Facebook.

for training purpose i annotate few data by labelme annotator.
after traing i get the bounding box for each pipe.

A) OUTPUT OF print(instances) fields=[pred_boxes, scores, pred_classes, pred_masks])

Explanation: this output says me there are 4 boxes detected.

B) OUTPUT OF print(instances.pred_boxes) Boxes(tensor([[289.3555, 17.8171, 451.1482, 347.6050], ]))

Explanation: this output says me, the coordinates of the boxes detected. In particular, the first box (instances.pred_boxes[0]) has the top_left point with coordinates (x,y)=(289.3555, 17.8171), and the bottom_right point with coordinates (x,y)=(451.1482, 347.6050)

C) OUTPUT OF print(instances.pred_boxes[0]) Boxes(tensor([[289.3555, 17.8171, 451.1482, 347.6050]])) Explanation: with this command, I just print the coordinates of the first box (instances.pred_boxes[0])

after getting the bounding box for each pipe ,I assume that the lenth of 
longest pipe is 50' ,then give the lengh of other pipe according to their proportion
,the sum total length.



#### problem face-
As can be seen from the drone shoots, there is significant overlap
between two consecutive frames, which may lead to duplicate
endpoints for a set of pipes in the two frames. How will you handle this
and ensure that each pipe has only two endpoints

for this problem i tried to stich the image in single frame.using cv2.Stitcher.
(failed due to this task is computationally expensive)
alternative way i though of solving this problem, after getting the boundind
box and length ,calculate the proportion for each pipe length in each image
then subtract the length of overlap image.
## Documentation

[Documentation](https://github.com/ravipratap366/PhotoGAUGE_assignment1-2/blob/main/PhotoGAUGE_final.pdf)

