# INSTALL

The environment for this artifact has been configured into a docker image and is available on docker hub:  [deekshaarya4/jupyter-scipy-nlp](https://cloud.docker.com/u/deekshaarya4/repository/docker/deekshaarya4/jupyter-scipy-nlp). Hence, this artifact assumes a running docker engine exists and that users are at least moderately familiar with docker. More information on downloading and getting started with docker can be found at: https://docs.docker.com/install/.

The data, code and results are provided externally and to be mounted into the image. This is done in order to allow easy interactive access to them, if necessary.

The docker image was created using a Docker Community Edition engine (version and engine 18.03.1-ce) on a macOS Mojave (version 10.14.2) operating system. It is built upon the *jupyter/scipy-notebook* provided by Project Jupyter. More information regarding the base image can be found [here](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html).

## Loading the Environment

1. First, start the docker service on your server.

> **Note:** Make sure no other jupyter server is running.

2. Navigate to inside the `Info_types_in_OSS_Issue_Discussions` folder in your terminal.

> **Note:** Before running the docker commands on Windows systems, you must ensure the following to allow the docker container access to the mounted directory:

> - When using _Docker Toolbox_: The `Info_types_in_OSS_Issue_Discussions` folder must be in `C:/Users`. This is because docker has limited access to directories in Windows.
> - When using _Docker Desktop_: You must allow the folder `Info_types_in_OSS_Issue_Discussions` to be shared. For instructions on how to do so, click  [here](https://docs.docker.com/docker-for-windows/troubleshoot/#shared-drives).

3. A docker container must be started and this repository must be mounted into the container. To do so and subsequently start the jupyter lab session to run the code, run the following in your terminal:

   **For Mac and Linux Systems:**

    `docker run --rm --user root -e NB_UID=$UID -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/ deekshaarya4/jupyter-scipy-nlp:v1 start.sh jupyter lab`

   **For Windows Systems:**

    `docker run --rm --user root -e NB_USER=jovyan -p 8888:8888 -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/home/jovyan/ deekshaarya4/jupyter-scipy-nlp:v1 start.sh jupyter lab`

   The above command will start the docker container and load the current directory into /home/jovyan from where the jupyter lab server will be up and running. The output in the terminal will display:

    ```
    Copy/paste this URL into your browser when you connect for the first time,
        to login with a token: <URL>
    ```

   Simply copy and paste the entire `<URL>` into your favorite browser to access the jupyter editor.

>**Note:** The `<URL>` may offer either a docker container ID or 127.0.0.1 as the hostname to use.

>For Mac and Linux systems, simply use `127.0.0.1`. Hence, the url to paste into your browser will be: `http://127.0.0.1:8888/?token=<TOKEN>`

>For Docker Toolbox (Legacy) on Windows systems, use `192.168.99.100`. This is the exposed IP of the Docker VirtualBox. You can verify this by running `docker-machine ip default` in your Windows terminal. Hence, the url to paste into your browser will be: `http://192.168.99.100:8888/?token=<TOKEN>`

## Testing the Installation

The best way to check if the installation is complete is to test the code functionality itself.

Open *test_environment.ipynb* and run all cells in order (You can navigate to the *Run* button on the Jupyter menu bar and click *Run All Cells*). This file reads from the file *all_data.pkl* that contains the preprocessed corpus, returns some statistics about the data in the file and performs some transformations on the data and saves them to a file. It the proceeds to create a basic machine learning model to predict the knowledge types of sentences. An error-free run of all the cells indicates a complete and successful installation.

This setup and test has been additionally verified:

1. using _Docker Desktop (version 2.0.0.2, engine 18.09.1)_ on _macOS Mojave (version 10.14.2)_

2. using _Docker Toolbox (engine 18.03.0-ce)_ on _Windows 10.0.17134.523 (Family)_

3. using _Docker (version 1.13.1)_ on _Ubuntu 16.04.4_
