# Ex05 Image Carousel
## Date:

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM

## App.js
```
import React from 'react';
import ImageCarousel from './ImageCarousel';
import './index.css';

function App() {
  return (
    <div className="carousel-container">
      <h1>React Image Carousel</h1>
      <ImageCarousel />
    </div>
  );
}

export default App;

```

## Index.css
```
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #d3e0dc, #f1f8f9);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.carousel-container {
  background-color: #ffffffcc;
  padding: 30px;
  border-radius: 16px;
  text-align: center;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.button-container {
  margin-top: 15px;
}

.button-container button {
  padding: 10px 20px;
  margin: 0 10px;
  background-color: #2c3e50;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

.button-container button:hover {
  background-color: #1a252f;
}

```
## ImageCarousel.js
```
import React, { useState, useEffect, useCallback } from 'react';

const images = [
  'https://wallpaperaccess.com/full/57061.jpg',
  'https://wallpaperaccess.com/full/1072539.jpg',
  'https://wallpaperaccess.com/full/198220.jpg'
];

function ImageCarousel() {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = useCallback(() => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  }, []);

  const prevImage = () => {
    setCurrentIndex((prevIndex) =>
      (prevIndex - 1 + images.length) % images.length
    );
  };

  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);
    return () => clearInterval(interval);
  }, [nextImage]);

  return (
    <div>
      <img
        src={images[currentIndex]}
        alt="carousel"
        style={{ width: '500px', borderRadius: '16px' }}
      />
      <div className="button-container">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
  );
}

export default ImageCarousel;
```
## OUTPUT
![image](https://github.com/user-attachments/assets/b33f20c9-44d8-4826-9c57-21327f0f7b19)
![image](https://github.com/user-attachments/assets/121bbe00-66a6-4b65-9a25-3c7c22f59a76)


## RESULT
The program for creating Image Carousel using React is executed successfully.
