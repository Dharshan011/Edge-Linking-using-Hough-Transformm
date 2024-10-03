# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## DEVELOPED BY: DHARSHAN V
## REG NO: 212222230031
## Output
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('HappyFish.jpg')  # Replace with your image path

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

```
![Screenshot 2024-10-03 160751](https://github.com/user-attachments/assets/bd1220e8-67cc-41a7-bed0-c6c94b8a9fb4)

### Input image and grayscale image
```
plt.subplot(2, 2, 2)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')

```

![Screenshot 2024-10-03 160756](https://github.com/user-attachments/assets/4a200118-59f5-491d-bdcd-220dfc7b644a)

### Canny Edge detector output
```
plt.subplot(2, 2, 3)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')
```

![Screenshot 2024-10-03 160800](https://github.com/user-attachments/assets/cd44f11f-aca8-4109-87d8-319c26ed14df)


### Display the result of Hough transform
```
# Hough Transform Result
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')

# Display all results
plt.show()

```
![Screenshot 2024-10-03 160804](https://github.com/user-attachments/assets/20d32d2f-8253-49ac-a26c-9a52b74e197e)


## Result:
Thus the program is written with python and OpenCV to detect lines using Hough transform.
