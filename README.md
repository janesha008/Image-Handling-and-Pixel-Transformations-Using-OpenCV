# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

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

## Program Developed By:
- **Name:** [Your Name Here]  
- **Register Number:** [Your Register Number Here]

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
img = cv2.imread('strawberry.jpg', cv2.IMREAD_GRAYSCALE)
```

#### 3. Display the image using matplotlib imshow().
```
height, width = img.shape

plt.imshow(img, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')
plt.show()

print("Width:", width)
print("Height:", height)
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
cv2.imwrite('strawberry.png', img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
img_color = cv2.imread('strawberry.jpg')
img_color = cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
height, width, channel = img_color.shape

plt.imshow(img_color)
plt.title('Color Image')
plt.axis('off')
plt.show()

print("Width:", width)
print("Height:", height)
print("Channels:", channel)
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
cropped_img = img_color[100:400, 100:400]

plt.imshow(cropped_img)
plt.title('Cropped Image')
plt.axis('off')
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```
resized_img = cv2.resize(cropped_img, None, fx=2, fy=2)

plt.imshow(resized_img)
plt.title('Resized Image')
plt.axis('off')
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```
flipped_img = cv2.flip(resized_img, 1)

plt.imshow(flipped_img)
plt.title('Horizontally Flipped Image')
plt.axis('off')
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```
apollo_img = cv2.imread('Apollo-11-launch.jpg')
apollo_img = cv2.cvtColor(apollo_img, cv2.COLOR_BGR2RGB)
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN

height, width, channel = apollo_img.shape
text_size = cv2.getTextSize(text, font_face, 1.5, 2)[0]
x = (width - text_size[0]) // 2
y = height - 20

cv2.putText(apollo_img, text, (x, y), font_face, 1.5, (255, 255, 255), 2)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
rect_color = (255, 0, 255)

cv2.rectangle(apollo_img, (200, 50), (600, 500), rect_color, 3)
```

#### 13. Display the final annotated image.
```
plt.imshow(apollo_img)
plt.title('Apollo 11 Launch')
plt.axis('off')
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```
img = cv2.imread('Boy.jpg')
```

#### 15. Adjust the brightness of the image.
```
matrix_ones = np.ones(img.shape, dtype='uint8') * 50
```

#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(img, matrix_ones)
img_darker = cv2.subtract(img, matrix_ones)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title('Darker Image')
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title('Brighter Image')
plt.axis('off')

plt.show()
```

#### 18. Modify the image contrast.
```
matrix1 = np.ones(img.shape, dtype='uint8') * 1.1
matrix2 = np.ones(img.shape, dtype='uint8') * 1.2

img_higher1 = cv2.convertScaleAbs(img, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(img, alpha=1.2, beta=0)

img_lower = cv2.convertScaleAbs(img, alpha=0.8, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(cv2.cvtColor(img_lower, cv2.COLOR_BGR2RGB))
plt.title('Lower Contrast')
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(img_higher1, cv2.COLOR_BGR2RGB))
plt.title('Higher Contrast')
plt.axis('off')

plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
B, G, R = cv2.split(img)

plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(B, cmap='gray')
plt.title('Blue Channel')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(G, cmap='gray')
plt.title('Green Channel')
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(R, cmap='gray')
plt.title('Red Channel')
plt.axis('off')

plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
merged_img = cv2.merge([B, G, R])

plt.figure(figsize=(8, 4))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged_img, cv2.COLOR_BGR2RGB))
plt.title('Merged RGB Image')
plt.axis('off')

plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

H, S, V = cv2.split(hsv_img)

plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(H, cmap='gray')
plt.title('Hue Channel')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(S, cmap='gray')
plt.title('Saturation Channel')
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(V, cmap='gray')
plt.title('Value Channel')
plt.axis('off')

plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.merge([H, S, V])
merged_bgr = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2BGR)

plt.figure(figsize=(8, 4))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged_bgr, cv2.COLOR_BGR2RGB))
plt.title('Merged HSV Image')
plt.axis('off')

plt.show()
```

## Output:
- **i)** Read and Display an Image.

   <img width="530" height="313" alt="image" src="https://github.com/user-attachments/assets/6aa78ed4-4d7d-4a9f-9d6d-5c9029eba277" />

- **ii)** Adjust Image Brightness.

  <img width="956" height="201" alt="image" src="https://github.com/user-attachments/assets/8e0d00f0-ae4c-4017-85f4-820952b98e07" />

- **iii)** Modify Image Contrast.

  <img width="958" height="193" alt="image" src="https://github.com/user-attachments/assets/e63b066b-7aa1-4ef1-818b-1bd5e9d5ff4e" />

- **iv)** Generate Third Image Using Bitwise Operations.

  <img width="959" height="302" alt="image" src="https://github.com/user-attachments/assets/d5e56bee-30f3-443d-90d2-6c42f00f6a41" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

