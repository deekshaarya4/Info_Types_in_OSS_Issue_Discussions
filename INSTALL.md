# INSTALL

The environment for this artifact has been configured into a docker image and is available on docker hub:  [deekshaarya4/jupyter-scipy-nlp](https://cloud.docker.com/u/deekshaarya4/repository/docker/deekshaarya4/jupyter-scipy-nlp). Hence, this artifact assumes a running docker engine exists and that users are at least moderately familiar with docker. More information on downloading and getting started with docker can be found at: https://docs.docker.com/install/.

The data, code and results are provided externally and to be mounted into the image. This is done in order to allow easy interactive access to them, if necessary.

The docker image was created using a Docker Community Edition engine (version 18.03.1-ce) on a macOS Mojave (10.14.2) operating system. It is built upon the *jupyter/scipy-notebook* provided by Project Jupyter. More information regarding the base image can be found [here](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html).

## Loading the Environment

First, start the docker service on your server.

_**Note:** Make sure no other jupyter server is running._

A docker container must be started and this repository must be mounted into the container. To do so and subsequently start the jupyter lab session to run the code, run the following in your terminal:

`docker run --rm --user root -e NB_UID=$UID -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/ deekshaarya4/jupyter-scipy-nlp:v1 start.sh jupyter lab`

The above command will start the docker container and load the current directory into /home/jovyan from where the jupyter lab server will be up and running. The output in the terminal will display:

`Copy/paste this URL into your browser when you connect for the first time,
    to login with a token: <URL>`

Simply copy and paste the entire URL into your favorite browser to access the jupyter editor. The hostname in the <URL> may offer a docker container ID or 127.0.0.1 as the hostname to use. In such a case, use 127.0.0.1.

For eg. if the following is displayed in the terminal:

`Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://(c2d1a31f60b8 or 127.0.0.1):8888/?token=<TOKEN>`

Type `http://127.0.0.1:8888/?token=<TOKEN>` into your favorite browser.

## Testing the Installation

The best way to check if the installation is complete is to test the code functionality itself.

Open *transform_features.ipynb* and run each cell (in order). This file reads from the file *all_data.pkl* that contains preprocessed data and converts categorical features into One-Hot Encoded features, among other transformations. This new, transformed feature set is saved in a file called *text_conv_data.pkl* in the data directory. An error-free run of all the cells indicates a complete installation.
