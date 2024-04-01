# Real Time Number Plate Recognition using CNN

To achieve this task, let's understand the architecture. We need to recognise the license plate, here specifically Indian, all the contries have different type of license plate character and shape of plate.
So, overall we need to detect the number plate first, then recognise the characters. We also have one more bifurcation in this i.e. all the vehicle have different shape and size of number plate.
In this task, we are focusing only for car, and any number plate which is of the shape and size of car's number plate in India. Once, we have the plate recognised we have to recognise the characters of the plate.
Finally, we have to feed these recognised numbers to a API which can give us the vehicle information.

## WorkFlow:

### Model Creation:

Image --> HaarCascade [indian_license_plate](https://github.com/AnonMrNone/indian_licenseplate_recognition/blob/master/indian_license_plate.xml) --> Extracted Plate --> Character Segmentation --> [DataSet of characters of Indian License Plate](https://github.com/AnonMrNone/indian_licenseplate_recognition/tree/master/data/data) --> CNN Model Training --> model.predict(character segmented) --> Extracted plate number

Here, HaarCascade will only detect the number plate of size and shape related to car's number plate.

### Model Testing:

Import model and necessary function --> New Image of Car --> HaarCascade --> Extracted Plate --> Character Segmentation --> model.predict(segmented character) --> API

### Final webapp for video stream

Import model and necessary function --> Take Video From user --> For each frame --> HaarCascade --> Extracted Plate --> Character Segmentation --> model.predict(segmented character) --> API --> Final Output on Webpage

### API used for getting vehicle information

http://www.carregistrationapi.in/

## How to train the model?

As discussed earlier we have to train the model to recognise the plate's characters i.e. alphabets and numbers. Creating such a model need few things which will be explained in here.
The standard procedure to extarct any objects from the image is by finding the contours.

### What are contours?

Contours can be simply explained as a curve joining all the continuous points (along the boundary), having same colour or intensity. The contours are a useful tool for shape analysis and object detection and recognition.
* For better accuracy, use binary images. So before finding contours, apply threshold or canny edge detection. Since OpenCV 3.2 and later, findContours() no longer modifies the image source.
* In OpenCV, finding contours is like finding white object from black background. So remember, object to be found should be white and background should be black.

Read more at: https://docs.opencv.org/4.5.2/d4/d73/tutorial_py_contours_begin.html

