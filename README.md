# face_detection
Utilised already built face detection algorithms on BGR images stored in text files

For this problem, we were presented with image files in .txt format. 
#### The 1st task that was done was to process and clean the .txt to be able to view an actual image.

To do this, I read the text file using pandas read_csv method using an empty space(' ') delimeter because we were told that there is a space between consecutive pixels in each row. Then i analyzed the 1st pixel element where i discovered each pixel element was enclosed in a string. I cleaned this using 5 steps:
1. Perform a split on each comma(,) to get each of the pixel value in the pixel element as a string using a lambda function
2. Loop through each row and column to convert each string pixel value to a float type.
3. Flatten all the pixel values to a new list
4. Convert the list to an array
5. Reshape the array to the original dimension of the image with the channel dimension included. The channel dimension used was **3** since we are working with colored (BGR) images.

After doing this, I was able to view the images.

#### The 2nd task was to pass the images to face detection algorithms and get the no of faces detected from each image

I used 3 different face detection algorithms to achieve this task, namely:
* Open CVs built in cascade classifier for face detection
* Histogram of Oriented Gradients(HOG) face detection model in Dlib
* CNN based face detector model in Dlib

##### For the 1st image
The Haar cascade classifier from opencv performed best in terms of both speed and accuracy because it was able to detect all 2 faces in 0.042s which was the shortest time when compared with the other 2 algorithms

##### For the 2nd image
The CNN based face detector model performed best in terms of accuracy because it was able to detect all 3 faces but in terms of speed, the HOG model performed the best as it took 0.035s to detect 2 out of the 3 faces. The CNN however took 1.017s

##### For the 3rd image
The CNN face detection model in Dlib(after converting the image to grayscale) performed best in terms of both speed and accuracy because it was able to detect all 5 faces in 0.246s which was the shortest time compared with the HOG model that detected 4/5 faces in 0.343s while the Haar cascade classifier model detected 4/5 faces in 0.433s. The cnn model when used without converting the image to grayscale performed very poorly only detecting 2/5 faces.


### From all the different images that was tested on, it was seen that the cnn face detection model in Dlib performed best in terms of accuracy but when looking at speed, the HoG seems to be the fastest algorithm, followed by Haar Cascade classifier and CNNs.
