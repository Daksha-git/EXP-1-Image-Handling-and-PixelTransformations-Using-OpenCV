# EXP-1-Image-Handling-and-PixelTransformations-Using-OpenCV

**Name**: DAKSHA C

**Register No**: 212224230048

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

### Step 1: Read and Display an Image

```python
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('my_photo.jpg', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
```

### Step 2: Draw Shapes and Add Text

#### 2.1 Draw a Line

```python
# Load the image
image = cv2.imread('my_photo.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)

# Display the image
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```

#### 2.2 Draw a Circle

```python
# Load the image
image = cv2.imread('my_photo.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img_rgb.shape

circle_img = cv2.circle(img_rgb,(400,300),150,(255,0,0),10) # cv2.circle(image, center, radius, color, thickness)

# Display the image
plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```

#### 2.3 Draw a Rectangle

```python
# Load the image
image = cv2.imread('my_photo.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img.shape

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (768, 600), (0, 0, 255), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)

# Display the image
plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
```

#### 2.4 Add Text to the Image

```python
# Load the image
image = cv2.imread('my_photo.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)


# Display the image
plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```

### Step 3: Color Space Conversion

```python
# Load the image
image = cv2.imread('my_photo.jpg') 

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")

# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")

# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")

# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")

# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
```

### Step 4: Pixel Manipulation

```python
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
```

### Step 5: Image Resizing

```python
image = cv2.imread('my_photo.jpg') 
image.shape

# Resize the image to half its size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)

# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

### Step 6: Image Cropping

```python
# Load the image
image = cv2.imread('my_photo.jpg')

image.shape

# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

### Step 7: Image Flipping

```python
# Load the image
image = cv2.imread('my_photo.jpg')

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")

# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```

---

## OUTPUT

#The following outputs are obtained:

# 1. Original image displayed using OpenCV and Matplotlib.


<img width="237" height="427" alt="Screenshot 2026-10-31 101456" src="https://github.com/user-attachments/assets/fa22f4ec-5c02-4087-b113-c83f8aaab3e8" />


# 2. Image with a line drawn from the top-left to the bottom-right.

<img width="272" height="467" alt="Screenshot 2026-10-31 101618" src="https://github.com/user-attachments/assets/3cd3a977-e162-4b22-a95a-6b5fc774a507" />


# 3. Image with a circle .

<img width="267" height="448" alt="Screenshot 2026-10-31 101701" src="https://github.com/user-attachments/assets/6e434b6a-f817-4b2d-ad70-c0927e578481" />



# 4. Image with a rectangle around its boundary.

<img width="273" height="470" alt="Screenshot 2026-10-31 101735" src="https://github.com/user-attachments/assets/2e816c70-baee-4c00-9dd3-eaec15f8356d" />


# 5. Image with the text "OpenCV Drawing".

<img width="286" height="466" alt="Screenshot 2026-10-31 101806" src="https://github.com/user-attachments/assets/695d2f8e-bfb2-46ac-aeeb-2646c125f791" />



# 6. HSV, grayscale, and YCrCb color space conversions.


<img width="262" height="456" alt="Screenshot 2026-10-31 101932" src="https://github.com/user-attachments/assets/6f44e4c2-4709-4a93-a0f3-bce81e8db3b5" />

<img width="258" height="470" alt="Screenshot 2026-10-31 102009" src="https://github.com/user-attachments/assets/724981d4-b7d6-446d-baa0-334b35aa8888" />

<img width="266" height="468" alt="Screenshot 2026-10-31 102028" src="https://github.com/user-attachments/assets/0bc14ac1-1053-49b9-8d8a-1dff87ceb518" />



# 7. Image converted from HSV back to RGB.


<img width="257" height="466" alt="Screenshot 2026-10-31 102110" src="https://github.com/user-attachments/assets/fb7d809d-5864-43eb-88b5-2ec7c3df0e1b" />



#8. Pixel value displayed and a white region added to the image.

<img width="345" height="467" alt="Screenshot 2026-10-31 102128" src="https://github.com/user-attachments/assets/838eec20-604b-4283-9e66-cd9de4f8b338" />



# 9. Image resized to half its original dimensions.

<img width="553" height="463" alt="Screenshot 2026-10-31 102149" src="https://github.com/user-attachments/assets/fa4ba1ec-c990-4a50-94fa-529720930e69" />




# 10. Cropped region of interest displayed.

<img width="453" height="463" alt="Screenshot 2026-10-31 102208" src="https://github.com/user-attachments/assets/4208845e-2704-4bd2-8ba5-3c800b377af8" />


# 11. Horizontally flipped image displayed.


<img width="273" height="453" alt="Screenshot 2026-10-31 102236" src="https://github.com/user-attachments/assets/5fb83925-f41e-4017-ba74-5c81b8fce73f" />


# 12. Vertically flipped image displayed.


<img width="271" height="461" alt="Screenshot 2026-10-31 102241" src="https://github.com/user-attachments/assets/049cd8c1-8c98-4587-afcb-5189a4bcff0d" />

## RESULT

Thus, image handling and pixel transformations were performed using Python, OpenCV, and Matplotlib. The experiment demonstrated image reading, shape drawing, text insertion, color space conversion, pixel manipulation, image resizing, cropping, flipping, and saving.

---

