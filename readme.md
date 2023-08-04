Urine Strip Analyzer - Alemeno - Shivanshu Mishra
===================

This project aims to analyze urine strip images and extract their corresponding colors. Several assumptions have been considered during its development:

1. The provided images are in the .jpg format.
2. The images have minimal noise, ensuring that colors are easily distinguishable to the human eye.

Tech Stack and Methodology 
----------

### Frontend

The Frontend of the application is developed using ReactJS, employing Vite as the build tool. Chakra UI serves as the component library, while Axios handles HTTP Requests.


### Backend 

The Backend server is constructed using FastAPI in Python with uvicorn as the ASGI server. FastAPI is chosen due to its suitability for projects with a limited number of API routes.

##### Colour Extractor

The extractColors.py file contains the primary logic for color extraction, which can be divided into three steps:

1. **Cropping** - This step removes the background to prevent interference with color detection.
2. **PreProcessing** - Utilizing a bilinear extrapolator, each pixel's value is replaced with the average value of the row, effectively removing artifacts like granular noise and dark patches.
    
3. **Segmentation** - The image is divided into small segments of size (2x2) pixels, extracted using a vertical offset to capture the color of each square. The average value of this (2x2) grid is used to determine the final RGB value of the square.



Setup
-----

### Local Setup

   
1. Navigate to the backend folder,install the required dependencies and start the webserver on port 8000
   
   ```
   $ cd ./backend/
   $ pip install -r requirements.txt
   $ uvicorn api:app
   ```

2. Navigate to the frontend folder,install the required dependencies and start the webapp on port 5173
   
   ```
   $ cd ../frontend/
   $ npm install
   $ npm run dev
   ````

3. In your browser Navigate to http://localhost:5173
