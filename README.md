# Face-recognition-using-face-recognition-library

Face recognition can be easily performed using face_recognition library which is built using dlib’s state-of-the-art face recognition. Dlib is a modern C++ toolkit containing machine learning algorithms and tools for creating complex software in C++ to solve real world problems. Since dlib is developed using the C based programming language we need to install CMake and Visual Studios with C++ environment for the face_ recognition library to work.

Using this library it's very easy to implement face recognition, there is no need to train the model and it also gives accurate prediction.

Libraries to install: Cmake, dlib, face_recognition, cv2, os and numpy. Also install Visual Studio--> Desktop development with C++

Very less lines of code is required when compared to opencv and tensorflow framework because there is no need to define any classifier and most of the things like face detection and finding Region Of Interest(ROI) take place at the backend and we need to only give the dataset and define a function to find the embeddings.

At the backend of face_recognition library the following steps takes place :

Step 1) Finding the face The method used for detection is called HOG (Histogram of Oriented Gradients). First the image is converted into grayscale because finding a face color is not a critical value. Every single pixel in the image is compared with the surrounding pixel to find out how dark the current pixel is. Then draw an arrow in all the directions of the pixels which are getting darker. Repeat the same process for all the pixels in the image and for all images given. These arrows are called Gradient. Next break up all the images into small squares of 16x16 each. Count the gradient point in the major direction and then replace the square in the image with a single arrow in the direction that had the most of the arrows facing. To find the face in an HOG image, we should find the part of the image that looks similar to a known HOG pattern which was extracted from a bunch of other training faces.

Step 2) Posing and Projecting Faces This is done by estimating face landmarks i.e,finding out 68 specific points on every face. After specifying the points, we will know where the eyes and mouth are located and rotate, scale and shear the image so that the eyes and mouth are centered.

Steps to implement the code:

Step 1) Import all the required libraries.

Step 2) Mention the dataset path. The main advantage in using face_recognition library is that there is no need to give lots of data. Just one image of each person is enough for recognition. Preferably frontal face images should be given in the folder.

Step 3) Reading all the images in the folder.

Step 4) Removing the extention of all the images.

Step 5) Define a function findencodings to encode all the images.

Step 6) Opencv reads the images in BGR format but face_recognition library reads the images in RGB format so we need to convert all the images from BGR to RGB.

Step 7) Encode all the images.

Encoding Faces - Deep Convolutional Neural Network is used to train the image to generate 128 measurements for each face. The training is done by using 3 face images, 2 images of the same person and the third one is of a different person. This is also called a single “Triplet” training step.

Step 8) VideoCapture(0) - initialise webcam . To read an image file use cv2.imread("image file")

Step 9) Resize the image captured from webcam.

Step 10) Using face_locations we are finding the co-ordinates of the detected face and encode it.

Step 11) Use a for loop to compare the encoded images in the folder mentioned earlier and the encoded image captured from the webcam.

Step 12) Using face_distance its finding out how similar the compared images are.

Step 13) Using MatchIndex we are mentioning the index of the images.

Step 14) If the compared images are same then we are creating a bounding box around the face and printing the name.

Step 15) Using imshow we are displaying the output.

This method can be used for recognising frontal images, non-frontal images, faces in dim light and for blocked faces.
