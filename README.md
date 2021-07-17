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
# 3- Setting up your camera
```
cap = cv2.VideoCapture(0)
cap.set(3,640) # Width
cap.set(4,480) # Height
```
# 4- Call classifier function
These commands will help to set the camera and load input videos 
```
while True:
    ret, img = cap.read()
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    faces = faceCascade.detectMultiScale(
        gray,
        scaleFactor=1.2,
        minNeighbors=5,
        minSize=(20, 20)
    )
  ```
   
 # 5- Detect the faces
You have to mark the face using a blue rectangle
 ```
 for (x,y,w,h) in faces:
    cv2.rectangle(img,(x,y),(x+w,y+h),(255,0,0),2)
    roi_gray = gray[y:y+h, x:x+w]
    roi_color = img[y:y+h, x:x+w]
   
 ```
 # 6- Detect the smiles
 You have to mark the smile using a green rectangle
 ```
 smile = smileCascade.detectMultiScale(
            roi_gray,
            scaleFactor=1.5,
            minNeighbors=15,
            minSize=(25, 25),
        )
    for (xx, yy, ww, hh) in smile:
        cv2.rectangle(roi_color, (xx, yy), (xx + ww, yy + hh), (0, 255, 0), 2)
 ```
 
 # 7- Detect the eyes
 You have to mark the eyes using a green rectangle
 ```
   for (ex, ey, ew, eh) in eyes:
        cv2.rectangle(roi_color, (ex, ey), (ex + ew, ey + eh), (0, 255, 0), 2)
 
```
# 8- Quit the program
```
k = cv2.waitKey(30) & 0xff
    if k == 27:  # click on ESC to quit
        msg = 'press ESC to quit'
        break
```
