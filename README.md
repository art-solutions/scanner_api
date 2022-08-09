# Simple Document Scanner in Android

There are a lot of document scanner apps for Android, some of which are open-source and provide better accuracy. The perks of using and extending this project are,

* The core idea behind this project was **simplicity**. The source code is easy to understand even for beginners in Android and they can easily familiarize themselves with it.
* The project utilizes the **latest Android libraries for Kotlin** like Coroutines, Room, Scoped Storage
* It provides two **options to deploy the document scanning service**. The Android app on the `main` branch uses an API to crop the documents whereas the Android app on the `on_device_scanning_app` performs detection on-device and works without any networking.
* You can learn how to use **OpenCV in Kotlin and its setup** by viewing the `on_device_scanning_app` branch.
* 


## Document Scanning API


The `api` branch contains the code for the API built using [FastAPI](https://fastapi.tiangolo.com/) in Python. First, install the required packages from `requirements.txt` in a Python virtual environment,

```
> python venv doc_scanning_env
> source doc_scanning_env/bin/activate
> ( doc_scanning_env ) pip install -r requirements.txt
```

### Using the API locally

To run the FastAPI server locally, use

```
> uvicorn main:app 
```
in the source code directory where `main.py` is located. Make sure that,

* **The mobile device on which the app is running and the computer on which the server runs, are connected to the same network.**
* **On Windows, make sure you turnoff the Firewall while testing the app.**

### Using the Streamlit app

You can also perform document scanning with the Streamlit app, that let's you upload your image and outputs the boundaries of the document. To run the Streamlit app locally, use,

```
> streamlit run app.py
```


### Building and running the Docker image

You can bundle the code in a Docker image and build it,

```
# Make sure you're in the source directory
> docker build --tag document_scanning_api .
```