# Face-Detection
In this project we will use Pycharm IDE and Python to detect the face 
# 1- Import opencv
use this command to import opencv
```
import cv2
```
if you faced a problem use this steps
1- File
2- Setting
3- Click on the project file you are working on
4- Project interpreter
5- Add ( opencv-python ) and install the package

# 2- Initalize opencv
Save the Haar cascade classifiers files from https://github.com/opencv/opencv/tree/master/data/haarcascades
```
faceCascade = cv2.CascadeClassifier('Cascades/haarcascades/HAARCASCADE_FRONTALFACE_DEFAULT.xml')
eye_cascade = cv2.CascadeClassifier('Cascades/haarcascades/HAARCASCADE_EYE.xml')
smileCascade = cv2.CascadeClassifier('Cascades/haarcascades/HAARCASCADE_SMILE.xml')
```

