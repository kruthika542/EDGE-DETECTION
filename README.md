# EDGE-DETECTION

## Aim
To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required
- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## ⚙️ Algorithm
Step 1:
Import all the necessary modules for the program.

Step 2:
Load an image using cv2.imread().

Step 3:
Convert the image to grayscale.

Step 4:
Apply Sobel operator using OpenCV to detect edges.

Step 5:
Apply Prewitt operator using custom kernels.

Step 6:
Apply Roberts operator using custom kernels.

Step 7:
Apply Laplacian operator using OpenCV.

Step 8:
Apply Canny edge detector using OpenCV.

Step 9:
Display all edge-detected images for comparison.

## Developed By
Name: Kruthika R
Register No: 212225240075

## Program

## 1.Import Libraries
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

## Read the image
```
img = cv2.imread('boy.jpg')

if img is None:
    print("Image not found")
else:
    print("Image loaded successfully")
```

## Convert to Grayscale
```
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

plt.imshow(gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()
```

## Sobel Edge Detection
```
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)

sobel = cv2.magnitude(sobel_x, sobel_y)

sobel = cv2.convertScaleAbs(sobel)

plt.imshow(sobel, cmap='gray')
plt.title("Sobel Edge Detection")
plt.axis('off')
plt.show()
```
## Prewitt Edge Detection
```
kernel_x = np.array([[-1, 0, 1],
                     [-1, 0, 1],
                     [-1, 0, 1]])

kernel_y = np.array([[-1, -1, -1],
                     [ 0,  0,  0],
                     [ 1,  1,  1]])

prewitt_x = cv2.filter2D(gray, -1, kernel_x)
prewitt_y = cv2.filter2D(gray, -1, kernel_y)

prewitt = cv2.addWeighted(prewitt_x, 0.5, prewitt_y, 0.5, 0)

plt.imshow(prewitt, cmap='gray')
plt.title("Prewitt Edge Detection")
plt.axis('off')
plt.show()
```
## Roberts Edge Detection
```
kernel_x = np.array([[1, 0],
                     [0, -1]])

kernel_y = np.array([[0, 1],
                     [-1, 0]])

roberts_x = cv2.filter2D(gray, cv2.CV_64F, kernel_x)
roberts_y = cv2.filter2D(gray, cv2.CV_64F, kernel_y)

roberts = cv2.magnitude(roberts_x, roberts_y)

roberts = cv2.convertScaleAbs(roberts)

plt.imshow(roberts, cmap='gray')
plt.title("Roberts Edge Detection")
plt.axis('off')
plt.show()
```
## Laplacian Edge Detection
```
laplacian = cv2.Laplacian(gray, cv2.CV_64F)

laplacian = cv2.convertScaleAbs(laplacian)

plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian Edge Detection")
plt.axis('off')
plt.show()
```
## Canny Edge Detection
```
canny = cv2.Canny(gray, 100, 200)

plt.imshow(canny, cmap='gray')
plt.title("Canny Edge Detection")
plt.axis('off')
plt.show()
```
## Display All Outputs Together
```
plt.figure(figsize=(15, 10))

images = [gray, sobel, prewitt, roberts, laplacian, canny]

titles = ['Original Grayscale', 'Sobel', 'Prewitt',
          'Roberts', 'Laplacian', 'Canny']

for i in range(6):
    plt.subplot(2, 3, i+1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
    plt.axis('off')

plt.tight_layout()
plt.show()
```
## Output

## Grayscale image
<img width="275" height="410" alt="image" src="https://github.com/user-attachments/assets/bc3cba6a-2824-4ca5-a2f5-7a8699d7d34a" />

## Sobel Edge Detection
<img width="260" height="402" alt="image" src="https://github.com/user-attachments/assets/2d97e00a-0941-4135-8fdb-e9db5cc665cf" />

## Prewitt Edge Detection
<img width="250" height="405" alt="image" src="https://github.com/user-attachments/assets/78920c39-4c40-45d6-b44c-bf3a2e36a3ca" />

## Roberts Edge Detection
<img width="251" height="401" alt="image" src="https://github.com/user-attachments/assets/00a2b11a-114b-4a7b-babd-7bd6687f76ae" />

## Laplacian Edge Detection
<img width="260" height="402" alt="image" src="https://github.com/user-attachments/assets/be82e80d-586d-4348-aaa1-895f2dd65bd3" />

## Canny Edge Detection
<img width="257" height="396" alt="image" src="https://github.com/user-attachments/assets/ea0599fe-6175-433e-9599-918ae207198e" />

## Display All Outputs Together
<img width="902" height="716" alt="image" src="https://github.com/user-attachments/assets/ba8441d6-d043-4633-b3cc-2b4935954575" />

## Result
Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
