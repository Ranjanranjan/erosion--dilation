# Implementation-of-Erosion-and-Dilation
## Aim
To implement Erosion and Dilation using Python and OpenCV.
## Software Required
1. Anaconda - Python 3.7
2. OpenCV
## Algorithm:

### Step1:
Apply the dilation operation on the image using cv2.dilate() with the same structuring element. Dilation will increase the size of the white regions (text) in the image, effectively reversing the effect of erosion

### Step2:
Initialize a blank image (100 pixels high and 400 pixels wide) using NumPy. The image should be a single-channel (grayscale) array filled with zeros (black).

### Step3:
Use OpenCV's cv2.putText() function to overlay the text "HYCINTH" on the blank image. Define the font style, position, font scale, color, and thickness for rendering the text.

### Step4:
Specify the size of the structuring element (e.g., 5x5 pixels) and create a rectangular structuring element using cv2.getStructuringElement(). This element will be used for the morphological operations.

### Step5:
Apply the erosion operation on the image using cv2.erode() with the defined structuring element. Erosion will reduce the size of the white regions (text) in the image.
 
## Program:

## Developed by: Ranjan K
## Reg No.:212222230116

# Create the Text using cv2.putText

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('/content/uiop.jpg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))

# Input Image and Grayscale Image
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')

# Display all results
plt.show()
```

<img width="349" alt="Screenshot 2024-10-05 at 11 50 55 AM" src="https://github.com/user-attachments/assets/a5a1d5bc-bbab-40f4-b2ae-f798b832ccb7">


# Create the structuring element
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('/content/uiop.jpg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))

plt.subplot(2, 2, 2)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')
# Display all results
plt.show()


```
<img width="349" alt="Screenshot 2024-10-05 at 11 51 56 AM" src="https://github.com/user-attachments/assets/cfc6a6b9-013f-4900-b693-603ac2268bfb">


# Erode the image

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('/content/uiop.jpg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))

# Canny Edge Detection Output
plt.subplot(2, 2, 3)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')
# Display all results
plt.show()

```
<img width="350" alt="Screenshot 2024-10-05 at 11 52 51 AM" src="https://github.com/user-attachments/assets/d68cd42c-948d-4e6d-8220-1f2a7be6579e">


# Dilate the image
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('/content/uiop.jpg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))

# Hough Transform Result
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')
# Display all results
plt.show()
```

<img width="350" alt="Screenshot 2024-10-05 at 11 53 36 AM" src="https://github.com/user-attachments/assets/f5346616-915c-4716-a1f9-e5b5ebe28b75">




## Result
Thus the generated text image is eroded and dilated using python and OpenCV.
