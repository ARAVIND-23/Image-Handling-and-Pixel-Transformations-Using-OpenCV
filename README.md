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
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
img =cv2.imread("pic1.jpg",cv2.IMREAD_COLOR")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

```

#### 2. Print the image width, height & Channel.
```python
img.shape

```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img)
plt.show()
img.shape
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
img=cv2.imread("pic1.jpg")
cv2.imwrite("Eagle.png",img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img=cv2.imread('pic1.png')
img_rgb = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img)
plt.show()
img.shape
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```

#### 8. Resize the image up by a factor of 2x.
```python
res= cv2.resize(crop,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img=cv2.imread("pic1.jpg",cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Vik", (300, 700),cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()  
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)  
```

#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```python
img =cv2.imread("pic1.jpg",cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```

#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img, m)
img_darker = cv2.subtract(img, m)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
 1. Read and Display an Image.
![pic1](https://github.com/user-attachments/assets/57875329-75bb-46af-a210-cc2e461626fa)





2. Display the image using matplotlib imshow().

   
<img width="697" height="403" alt="image" src="https://github.com/user-attachments/assets/7c588a4c-5c51-43dc-a812-9f3b9ad70794" />




3)Resize the image up by a factor of 2x.

<img width="387" height="517" alt="image" src="https://github.com/user-attachments/assets/ca961e91-e89e-44a9-b0af-63bd9b89ccc9" />




4)Flipped Horizontally

<img width="474" height="517" alt="Screenshot 2026-02-03 111504" src="https://github.com/user-attachments/assets/3fe5726e-9c9a-4bd5-8acc-5dc64a5e9314" />





5)New image.


<img width="682" height="425" alt="image" src="https://github.com/user-attachments/assets/b67949e7-9c54-4fcd-a03e-361bd956d6ec" />


6)Annotated image.

<img width="691" height="427" alt="Screenshot 2026-02-03 111702" src="https://github.com/user-attachments/assets/f8ca4b58-2006-4ea6-9a77-958726a8ffeb" />


7)Brightness.

<img width="1025" height="225" alt="Screenshot 2026-02-03 111825" src="https://github.com/user-attachments/assets/b0774b18-14b2-4abb-98fc-2a02cef2c9d3" />



8)Contrast.
<img width="972" height="202" alt="image" src="https://github.com/user-attachments/assets/ff36ff2f-cd8a-4bb5-99a9-8e90c9241ec5" />




9)BGR Channel.

<img width="981" height="200" alt="Screenshot 2026-02-03 113037" src="https://github.com/user-attachments/assets/659a8a9b-816e-473c-9e03-c4a471ac32ef" />




10)Hue Channel.

<img width="973" height="207" alt="Screenshot 2026-02-03 113545" src="https://github.com/user-attachments/assets/cf886431-9d82-4fc3-84df-c956ade56663" />



11) Merged HSV Image.

<img width="1011" height="316" alt="image" src="https://github.com/user-attachments/assets/53e4aaea-4881-48a5-bc14-4ebc1185fa0d" />



12)Merge the R, G, B channels and display:



<img width="981" height="200" alt="Screenshot 2026-02-03 113037" src="https://github.com/user-attachments/assets/e0fc2392-09e9-4cb6-81c0-fd4c929d5270" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

