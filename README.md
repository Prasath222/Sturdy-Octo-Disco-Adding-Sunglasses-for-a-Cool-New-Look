# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

  ## PROGRAM:
Developed by: HARI PRASATH P
Register Number: 212224230084

```
# Import libraries and Load the Face Image
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage = cv2.imread('643.JPG')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
```
![5fe2e4db-6ff9-4d68-8f00-3bdd72f06272](https://github.com/user-attachments/assets/093f63ac-c663-4e7a-a4b6-49f9c5caa607)


```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))
```
![b556a937-976a-44aa-9386-f0f46e9128d4](https://github.com/user-attachments/assets/7f1375ed-3a79-424f-b592-7f08c72df793)


```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))

# Separate the Color and alpha channels
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

# Display the images for clarity
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
```
![e9c1ea51-b71e-4734-930a-79d6adcf7db8](https://github.com/user-attachments/assets/db17c215-053a-4784-85f4-188055b4d989)


```
faceWithGlassesNaive = faceImage.copy()
# Replace the eye region with the sunglass image
faceWithGlassesNaive[150:220, 120:310]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])
```
![24e3f720-d9ee-439e-aa36-7fcbe3682fca](https://github.com/user-attachments/assets/ec233c05-3a2c-4d48-9180-3135c7c00546)


```
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[150:220, 120:310]
maskedEye = cv2.multiply(eyeROI,(1-glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```
![511b4ee3-3047-4fc9-8c4a-7a41d1684a0f](https://github.com/user-attachments/assets/8b54d445-cc65-4b39-8e4f-91f209910c22)


```
faceWithGlassesArithmetic[150:220, 120:310]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```
![a46fbbcb-9b9f-4692-bce6-8853e4fbfe75](https://github.com/user-attachments/assets/0099614b-88b5-40d9-8e0c-0041d9a283d4)
 


