## Read Image
from[here](http://www.learnopencv.com/read-an-image-in-opencv-python-cpp/)

```python
image = cv2.imread(filename, flags=cv2.IMREAD_COLOR)

#without alpha channel
image = cv2.imread("image.jpg")

#Gray scale
image = cv2.imread("image.jpg", cv2.IMREAD_GRAYSCALE)

#16bit(higher depth)
img = cv2.imread("image.png", cv2.IMREAD_ANYCOLOR | cv2.IMREAD_ANYDEPTH)

#transparent tiff or png
img = cv2.imread("image.png", cv2.IMREAD_UNCHANGED)
```



## How to find frame rate?
from[here](http://www.learnopencv.com/how-to-find-frame-rate-or-frames-per-second-fps-in-opencv-python-cpp/)

### Video file
```python
import cv2
if __name__ == '__main__' :
 
    video = cv2.VideoCapture("video.mp4");
     
    # Find OpenCV version
    (major_ver, minor_ver, subminor_ver) = (cv2.__version__).split('.')
     
    if int(major_ver)  < 3 :
        fps = video.get(cv2.cv.CV_CAP_PROP_FPS)
        print "Frames per second using video.get(cv2.cv.CV_CAP_PROP_FPS): {0}".format(fps)
    else :
        fps = video.get(cv2.CAP_PROP_FPS)
        print "Frames per second using video.get(cv2.CAP_PROP_FPS) : {0}".format(fps)
     
   video.release(); 
```

### Camera
```python
#!/usr/bin/env python
 
import cv2
import time
 
if __name__ == '__main__' :
 
    # Start default camera
    video = cv2.VideoCapture(0);
     
    # Find OpenCV version
    (major_ver, minor_ver, subminor_ver) = (cv2.__version__).split('.')
     
    # With webcam get(CV_CAP_PROP_FPS) does not work.
    # Let's see for ourselves.
     
    if int(major_ver)  < 3 :
        fps = video.get(cv2.cv.CV_CAP_PROP_FPS)
        print "Frames per second using video.get(cv2.cv.CV_CAP_PROP_FPS): {0}".format(fps)
    else :
        fps = video.get(cv2.CAP_PROP_FPS)
        print "Frames per second using video.get(cv2.CAP_PROP_FPS) : {0}".format(fps)
     
 
    # Number of frames to capture
    num_frames = 120;
     
     
    print "Capturing {0} frames".format(num_frames)
 
    # Start time
    start = time.time()
     
    # Grab a few frames
    for i in xrange(0, num_frames) :
        ret, frame = video.read()
 
     
    # End time
    end = time.time()
 
    # Time elapsed
    seconds = end - start
    print "Time taken : {0} seconds".format(seconds)
 
    # Calculate frames per second
    fps  = num_frames / seconds;
    print "Estimated frames per second : {0}".format(fps);
 
    # Release video
    video.release()
```
