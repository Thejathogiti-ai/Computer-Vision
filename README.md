# Computer-Vision
👁️ Face & Eye Detection using OpenCV (Haar Cascade)

Project Overview

This project demonstrates a classical Computer Vision approach for detecting human faces and eyes using OpenCV's Haar Cascade classifiers. The objective was to understand the complete detection pipeline, beginning with loading an image, preprocessing it, detecting faces, identifying the eye region within each detected face, and finally extending the same approach to live webcam video.

Although modern deep learning models are widely used today, Haar Cascades remain an important concept because they are lightweight, computationally efficient, and commonly discussed in Computer Vision interviews to explain the evolution of object detection techniques.

---

Business Problem

Many real-world applications require the ability to quickly detect faces before performing more advanced tasks such as identity verification or facial analysis.

Some common applications include:

- Face unlock systems
- Attendance monitoring
- Driver monitoring systems
- Video surveillance
- Camera autofocus
- Human-computer interaction

This project focuses only on detecting the location of faces and eyes rather than recognizing who the person is.

---

Dataset

Instead of using a structured dataset, this project uses:

- A sample image for face and eye detection
- Live webcam frames for real-time detection
- Pre-trained Haar Cascade XML files provided by OpenCV

No model training was required because the classifiers were already trained by OpenCV.

---

Project Workflow

1. Import Required Libraries

The project begins by importing:

- OpenCV ("cv2")
- Matplotlib
- PIL
- OS module

These libraries are used for image loading, visualization, and accessing Haar Cascade files.

---

2. Load Haar Cascade Classifiers

Two pre-trained classifiers were loaded:

- "haarcascade_frontalface_default.xml" for face detection
- "haarcascade_eye.xml" for eye detection

These XML files contain features learned from thousands of positive and negative training images.

---

3. Read the Image

The input image was loaded using OpenCV.

Since OpenCV reads images in BGR format, the image was converted to RGB before visualization using Matplotlib.

---

4. Convert Image to Grayscale

The image was converted from color to grayscale because Haar Cascade classifiers operate only on grayscale images.

Using grayscale reduces computational complexity while preserving the structural information required for object detection.

---

5. Detect Faces

Faces were detected using the "detectMultiScale()" method.

The important parameters used were:

- scaleFactor – Controls image scaling while searching for faces of different sizes.
- minNeighbors – Reduces false detections by requiring multiple neighboring detections.
- minSize – Specifies the minimum detectable face size.

The detector returns the coordinates:

- x
- y
- width
- height

for every detected face.

---

6. Draw Bounding Boxes

A rectangle was drawn around every detected face using OpenCV's "rectangle()" function to visualize the detection results.

---

7. Detect Eyes

Instead of searching the entire image, eye detection was performed only inside the detected face.

The detected face region was extracted as a Region of Interest (ROI).

Running eye detection inside the ROI improves efficiency and significantly reduces false detections.

Detected eyes were highlighted with green rectangles.

---

8. Real-Time Face & Eye Detection

The same pipeline was extended to webcam video.

For every frame:

- Capture frame from webcam
- Convert to grayscale
- Detect faces
- Detect eyes within each detected face
- Draw rectangles
- Display the processed frame continuously until the camera is closed

---

Technologies Used

- Python
- OpenCV
- Haar Cascade Classifiers
- Matplotlib
- PIL

---

Key Computer Vision Concepts Learned

- Image preprocessing
- BGR to RGB conversion
- Grayscale conversion
- Haar Cascade classifiers
- Feature-based object detection
- Region of Interest (ROI)
- Bounding boxes
- Multi-scale object detection
- Real-time webcam processing

---

Challenges

- Haar Cascades only work on grayscale images.
- Detection accuracy is affected by lighting conditions, face orientation, and occlusions.
- Parameter tuning ("scaleFactor" and "minNeighbors") is important to balance missed detections and false positives.
- Eye detection over the full image can produce unnecessary detections, so restricting the search to the detected face ROI improves performance.

---

Results

The implemented pipeline successfully:

- Detected human faces in static images.
- Detected eyes within each detected face.
- Drew bounding boxes around detected objects.
- Performed real-time face and eye detection using a webcam.
- Demonstrated the complete traditional Computer Vision detection workflow without training a custom model.

---

