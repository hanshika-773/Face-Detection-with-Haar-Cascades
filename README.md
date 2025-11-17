

## **📌 Project Overview**

This project demonstrates **face and eye detection** using **OpenCV's Haar Cascade Classifiers**.
The script loads grayscale images, resizes them, displays them, and then applies:

* **Face detection** using `haarcascade_frontalface_default.xml`
* **Eye detection** using `haarcascade_eye.xml`

It also includes a final block to run face detection on a custom static image.

---

## **📁 Project Structure**

```
face_detections.py
haarcascade_frontalface_default.xml
haarcascade_eye.xml
image_01.png
image_02.png
image_03.png
(optional) WIN_20251117_11_34_42_Pro.jpg
```

---

## **🚀 Features**

* Load and display multiple grayscale images.
* Resize images for uniform appearance.
* Detect and highlight **faces** using Haar Cascades.
* Detect and highlight **eyes** using Haar Cascades.
* Display results using Matplotlib.
* Accepts & processes custom images.

---

## **🔧 Requirements**

Install required libraries:

```bash
pip install opencv-python matplotlib numpy
```

If running in **Google Colab**, the script also uses:

```python
from google.colab.patches import cv2_imshow
```

---

## **📥 How It Works**

### **1. Load Images**

The code reads 3 sample images in grayscale:

```python
img1 = cv2.imread("/content/image_01.png", cv2.IMREAD_GRAYSCALE)
```

### **2. Display Images**

Using Matplotlib:

```python
plt.imshow(img1, cmap="gray")
```

### **3. Resize Images**

Each image is resized to 600×600 pixels:

```python
resized1 = cv2.resize(img1, (600, 600))
```

### **4. Face Detection**

Using Haar Cascade:

```python
face_cascade = cv2.CascadeClassifier("haarcascade_frontalface_default.xml")
```

A function is defined:

```python
def detect_face(img):
    face_rect = face_cascade.detectMultiScale(img)
    for (x,y,w,h) in face_rect:
        cv2.rectangle(img, (x,y), (x+w, y+h), (255,255,0), 10)
    return img
```

### **5. Eye Detection**

Using another cascade:

```python
eye_cascade = cv2.CascadeClassifier("haarcascade_eye.xml")
```

```python
def detect_eye(img):
    rect = eye_cascade.detectMultiScale(img)
```

### **6. Custom Image Detection**

You can replace this path with any image:

```python
image_path = "/content/WIN_20251117_11_34_42_Pro.jpg"
```

---

## **📷 Output**

The script displays:

* Original images
* Resized images
* Face detection bounding boxes
* Eye detection bounding boxes

Each output is shown using Matplotlib or `cv2_imshow()` (for Colab).

---

## **📝 Notes**

* Haar Cascades work best on clear, frontal faces.
* Lighting and image quality affect accuracy.
* Cascades must be placed in the same folder as the script.

---

## **▶️ Running the Code**

Run the script:

```bash
python face_detections.py
```

To test with another image, modify:

```python
image_path = "/content/your_image.jpg"
```

---

## **📚 References**

* OpenCV documentation
* Haar Cascade classifiers dataset
