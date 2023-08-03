Urine Strip Analyzer - Alemeno 
===================

This Project can analyze images of urine strips and extract the associated colors from the image. The following assumptions have been taken into account -

1. The supplied image is in .jpg format
2. The image is not very noise , i.e colors are distinguishable with human eye

Tech Stack and Methodology 
----------

### Frontend

The Frontend is built using ReactJS with Vite as a build took . Chakra UI is used as the component library and Axios is used for making HTTP Requests.


### Backend 

The Backend server is built using FastAPI in python using uvicorn as the ASGI server. The choice of FastAPI as a framework is because the scope of the project requires small number of API routes.

##### Colour Extractor

The extractColors.py file contains the main logic for the color extraction. The process can be divided into three steps :-

1. **Cropping** - Cropping is done to remove the background as it can interfere with the color detection
2. **PreProcessing** - A billinear extrapolator is used to replace value of each pixel with the average value of the row to remove artifacts like granular noise and dark patches
    
3. **Segmentation** - small segements of size (2x2) pixels are extracted from the image using a vertical offset to get the color from each sqaure and the average value of this (2x2) grid is used to determine the final RGB value of the square



Setup
-----

### Bare Metal Setup

1. Clone this repository using 
   
   ```
   $ git clone 
   ```
2. Navigate to the backend folder,install the required dependencies and start the webserver on port 8000
   
   ```
   $ cd ./backend/
   $ pip install -r requirements.txt
   $ uvicorn api:app
   ```

3. Navigate to the frontend folder,install the required dependencies and start the webapp on port 5173
   
   ```
   $ cd ../frontend/
   $ npm install
   $ npm run dev
   ````

4. In your browser Navigate to http://localhost:5173


### Using docker-compose and Docker

1. If you have Docker and docker-compose installed on your system just navigate to the root of the project and run 

   ```
   $ docker compose up
   ```

2. In your browser Navigate to http://localhost:5173


