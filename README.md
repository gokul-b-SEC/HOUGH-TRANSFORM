# Record – Hough Transform

## Aim

To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

## Learning Objectives

- Understand each stage of image processing.
- Learn how to build a complete computer vision pipeline.
- Practice writing code in guided sections.

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## Algorithm and Explanation

**Step 1: Import Libraries**

Import the required libraries: OpenCV, NumPy, and Matplotlib.

**Step 2: Read the Image**

Load the input image from the local directory using `cv2.imread()`.

**Step 3: Convert to Grayscale**

Convert the input image from BGR to grayscale using `cv2.cvtColor()`.

**Step 4: Display Images**

Display the original image and grayscale image using Matplotlib.

**Step 5: Edge Detection (Canny)**

Apply the Canny edge detector using `cv2.Canny()` with lower and upper threshold values of 50 and 150.

**Step 6: Hough Transform**

Use `cv2.HoughLinesP()` to detect straight-line segments in the edge-detected image.

**Step 7: Draw Detected Lines**

Draw the detected lines on the original image using `cv2.line()`.

**Step 8: Display the Result**

Display the final image with the detected lines highlighted in green.

## Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
image = cv2.imread(
    r"C:\Users\acer\Pictures\Screenshots\LUDO.png"
)

# Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
plt.show()

# Display the grayscale image
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

# Apply Canny Edge Detection
edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
plt.show()

# Apply Probabilistic Hough Transform
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)

# Draw detected lines on the original image
for line in lines:
    x1, y1, x2, y2 = line[0]
    cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Display the final image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
plt.show()
```

## Output

The following outputs demonstrate the stages of the Hough Transform implementation.

### 1. Input Image

<img width="366" height="376" alt="image" src="https://github.com/user-attachments/assets/1a9de738-95b9-4eb3-aaff-81c6d00b5d0d" />


### 2. Grayscale Image

<img width="376" height="380" alt="image" src="https://github.com/user-attachments/assets/31fa930d-4651-48df-bd95-6afc9d788443" />


### 3. Canny Edge Detection

<img width="363" height="380" alt="image" src="https://github.com/user-attachments/assets/899af09c-a330-46b5-b6c8-ef1c936aa93f" />


### 4. Result of Hough Transform

<img width="370" height="375" alt="image" src="https://github.com/user-attachments/assets/f75edd31-5acc-4bee-8580-3134629bb075" />


## Result

Thus, the Hough Transform pipeline was successfully implemented using OpenCV. The input image was converted into grayscale, edges were detected using the Canny edge detector, and straight-line segments were identified using the Probabilistic Hough Transform and highlighted in green.
