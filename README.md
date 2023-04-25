# cloud-native-monitoring-app

Navigate to master branch to see contents.

The application uses the **`psutil`** and **`Flask`, Plotly, boto3** libraries. Install them using pip:

On terminal: pip3 install -r requirements.txt


### **Run the application**

To run the application, navigate to the root directory of the project and execute the following command:

$ python3 app.py


This will start the Flask server on **`localhost:5000`**. Navigate to [http://localhost:5000/](http://localhost:5000/) on your browser to access the application.

## **Dockerizing the Flask application**

### **Step 1: Create a Dockerfile**

Create a **`Dockerfile`** in the root directory of the project with the following contents:

Use the official Python image as the base image
FROM python:3.9-slim-buster

Set the working directory in the container
WORKDIR /app

Copy the requirements file to the working directory
COPY requirements.txt .

RUN pip3 install --no-cache-dir -r requirements.txt

Copy the application code to the working directory
COPY . .

Set the environment variables for the Flask app
ENV FLASK_RUN_HOST=0.0.0.0

Expose the port on which the Flask app will run
EXPOSE 5000

Start the Flask app when the container is run
CMD ["flask", "run"]


### **Step 2: Build the Docker image**

To build the Docker image, execute the following command:

$ docker build -t <image_name> .


### **Step 3: Run the Docker container**

To run the Docker container, execute the following command:

$ docker run -p 5000:5000 <image_name>


This will start the Flask server in a Docker container on **`localhost:5000`**. Navigate to [http://localhost:5000/](http://localhost:5000/) on your browser to access the application.
