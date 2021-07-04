# Detecting Ocular Myopathy with Deep Learning from OCT Patient Scans

![MIT](https://img.shields.io/github/license/djvaroli/samsung_oct)
[![Python 3.8](https://img.shields.io/badge/python-3.6-blue.svg)](https://www.python.org/downloads/release/python-360/)


## About
In this repo you will find the source code, along with EDA notebooks and some (but not all) models used to create the `Molo` application for detecting ocular myopathies from OCT scans.

Authors: Kevin De Jesus, Janhavi Giri and Daniel Varoli

## Overview
The full app is split into 2 services:

* The frontend
* The backend (called molo). 
Earlier versions of the app also had a third service, the Tensorflow Serving service, however that has been removed in the latest
version of the application. The reason was the need for the gradients generated by the model, so as a result the model is loaded in at boot time.
This is perhaps not the best way to achieve the necessary, goal, however for the time being this was the best way we could come up with. 

In future versions of the app, we hope to switch back to serving models with Tensorflow Serving as that is much cleaner and more efficient.

Currently the production version of this application is hosted on GCP Cloud Run and can be found at [here](https://samsung-oct-frontend-ckxu3m5cka-uc.a.run.app/)

## Demo
A quick demo of what the app looks like at the moment. To run that locally for you, just follow the instructions
further down.

![MOLO Demo](.github/readme-assets/demo.gif)

## Running Locally with Docker
The good news is is that this repo comes with a `docker-compose` file, which you can use to run the entire app on any machine with Docker installed.
(To install Docker click [here](https://docs.docker.com/get-docker/)

Once you have Docker installed, clone this repo 

```bash
mkdir samsung_oct && git clone https://github.com/djvaroli/samsung_oct.git samsung_oct/
```

Navigate to the root directory of the repo. 

```bash
cd samsung_oct/
```

Boot up the two services with `docker-compose`
```bash
docker-compose up --build
```

You should now be able to access the `molo` service at `localhost:8000` and the frontend service at `localhost:80`. 
To make sure things are working, navigate to `localhost:8000` and you should see a welcome message.

## Set-up with Python Venv
Clone this repository to your local machine
```bash
mkdir samsung_oct && git clone https://github.com/djvaroli/samsung_oct.git samsung_oct/
```

Create a python virtual environment and activate it
```bash
python3 -m venv venv && source venv/bin/activate
```

Install all the necessary dependencies
```bash
pip3 install -r requirements.txt
pip3 install -e utilities/ # this will install the  custom utility functions
```

You should now be set to run/modify code in this repository. 
