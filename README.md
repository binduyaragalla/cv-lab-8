LAB-8: Harris Corner Detection

Aim

To implement Harris Corner Detection for identifying corner points in an image.


Description

Harris Corner Detection is a computer vision technique used to identify corners in an image. Corners are points where the intensity changes significantly in multiple directions. The algorithm uses intensity gradients and a corner response function to detect these points. The detected corners are marked on the original image for visualization.


Libraries Used

NumPy: For numerical operations and array manipulation.

OpenCV (cv2): For image loading, grayscale conversion, and Harris Corner Detection.

Matplotlib (pyplot): For displaying the input and output images.


Input Image

<img width="335" height="597" alt="image" src="https://github.com/user-attachments/assets/eb86d3ce-4893-4c59-a005-f903bd52a812" />

The original image used for detecting corner points.


Code

import cv2
import numpy as np
import matplotlib.pyplot as plt


def show_image(title, img, cmap=None):
    plt.figure(figsize=(8, 8))
    plt.title(title)

    if cmap:
        plt.imshow(img, cmap=cmap)
    else:
        plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))

    plt.axis('off')
    plt.show()


img = cv2.imread('input_image.jpg')

if img is None:
    print("Error: Image not found.")
else:
    
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    
    gray = np.float32(gray)

   
    dst = cv2.cornerHarris(gray, 2, 3, 0.04)

   
    dst = cv2.dilate(dst, None)

   
    img[dst > 0.01 * dst.max()] = [0, 0, 255]

   
    show_image("Harris Corner Detection", img)

Output Image

<img width="365" height="658" alt="image" src="https://github.com/user-attachments/assets/96da3261-19d9-4500-94ca-2649247d3478" />


The output image displays the detected corner points marked in red on the original image. These points represent locations where intensity changes significantly in multiple directions.


Result

Harris Corner Detection was successfully implemented using Python and OpenCV. The algorithm detected corner points in the input image and highlighted them in red.


Conclusion

Harris Corner Detection identifies important corner features by analyzing intensity changes in different directions. It is useful in image matching, object tracking, feature detection, and computer vision applications.
