<img width="1191" height="796" alt="image" src="https://github.com/user-attachments/assets/216fdd41-21ec-40b1-85fe-ac45dec4ed36" /># Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---



### Developed By:
**Name:** DEEPAKKUMAR S 

### Register No: 212225230042

##  Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Read the image in grayscale
img = cv2.imread('pic.png', 0)

if img is None:
    print("Image not found!")
    exit()

# Step 2: Display original grayscale image and histogram
plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(img, cmap='gray')
plt.title('Original Grayscale Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.hist(img.ravel(), 256, [0, 256])
plt.title('Original Grayscale Histogram')

# Step 3: Apply histogram equalization
equalized = cv2.equalizeHist(img)

plt.subplot(2, 2, 3)
plt.imshow(equalized, cmap='gray')
plt.title('Enhanced Grayscale Image')
plt.axis('off')

plt.subplot(2, 2, 4)
plt.hist(equalized.ravel(), 256, [0, 256])
plt.title('Enhanced Grayscale Histogram')

plt.tight_layout()
plt.show()

# Step 4: Read the image in color format
color_img = cv2.imread('pic.png')

if color_img is None:
    print("Color image not found!")
    exit()

# Step 5: Split the image into B, G, R channels
b, g, r = cv2.split(color_img)

# Step 6: Plot B, G, R channel histograms
plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(color_img, cv2.COLOR_BGR2RGB))
plt.title('Original Color Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.hist(b.ravel(), 256, [0, 256], color='blue')
plt.title('Blue Channel Histogram')

plt.subplot(2, 2, 3)
plt.hist(g.ravel(), 256, [0, 256], color='green')
plt.title('Green Channel Histogram')

plt.subplot(2, 2, 4)
plt.hist(r.ravel(), 256, [0, 256], color='red')
plt.title('Red Channel Histogram')

plt.tight_layout()
plt.show()

# Step 7: Convert BGR to HSV
hsv = cv2.cvtColor(color_img, cv2.COLOR_BGR2HSV)

# Step 8: Split HSV channels
h, s, v = cv2.split(hsv)

# Step 9: Apply histogram equalization to V channel
v_equalized = cv2.equalizeHist(v)

# Step 10: Merge channels and convert HSV back to BGR
hsv_equalized = cv2.merge((h, s, v_equalized))
enhanced_color = cv2.cvtColor(hsv_equalized, cv2.COLOR_HSV2BGR)

# Step 11: Display original color image, histogram,
# enhanced image, and enhanced histogram
plt.figure(figsize=(10, 8))

plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(color_img, cv2.COLOR_BGR2RGB))
plt.title('Original Color Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.hist(color_img.ravel(), 256, [0, 256])
plt.title('Original Color Histogram')

plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(enhanced_color, cv2.COLOR_BGR2RGB))
plt.title('Enhanced Color Image')
plt.axis('off')

plt.subplot(2, 2, 4)
plt.hist(enhanced_color.ravel(), 256, [0, 256])
plt.title('Enhanced Color Histogram')

plt.tight_layout()
plt.show()

```

##  Output
<img width="1362" height="511" alt="Screenshot 2026-10-27 215810" src="https://github.com/user-attachments/assets/d5891826-22b3-44a6-96bf-147b64e5f3b7" />
<img width="1382" height="517" alt="Screenshot 2026-10-27 215826" src="https://github.com/user-attachments/assets/91d78aac-c617-4b9b-a675-fbf03670dc20" />
<img width="1402" height="468" alt="Screenshot 2026-10-27 215842" src="https://github.com/user-attachments/assets/d7678307-d9c3-4f7d-be67-b3fea6b72dcb" />
<img width="1408" height="527" alt="Screenshot 2026-10-27 215857" src="https://github.com/user-attachments/assets/da15da1f-71bc-4eca-9d4b-38ed92576490" />
<img width="1191" height="796" alt="Screenshot 2026-10-27 215946" src="https://github.com/user-attachments/assets/c93c87b4-796f-408f-aab5-fa7dd11f9fb7" />



### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
