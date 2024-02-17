# Jupyter Custom Docker Setup

This repository contains a Docker Compose configuration along with two Dockerfiles to set up a custom Jupyter environment with additional Python libraries.

## Prerequisites

Before you begin, ensure you have Docker and Docker Compose installed on your system.

## Usage

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/AYMNrh/jupyter-custom.git
   ```
2. Navigate to the cloned repository:

   ```bash
   cd jupyter-custom
   ```
3. Build and start the Docker containers using Docker Compose:

   ```bash
   docker_compose up
   ```
4. Once the containers are running, you can access the Jupyter Notebook interface by opening a web browser and navigating to `http://localhost:8888`.

5. When prompted, enter the token displayed in the terminal to log in to Jupyter Notebook.

# Docker Compose Configuration

The docker-compose.yml file defines two services:

* `python-libraries`: Builds a Docker container based on the `Dockerfile.libraries` file. It installs Python libraries listed in the `requirements.txt` file into a volume named `jupyter-libraries`.

* `jupyter`: Builds a Docker container based on the `Dockerfile.jupyter` file. It sets up a Jupyter environment with SciPy and exposes port 8888. It also mounts the `notebooks` directory from the host machine and the `jupyter-libraries` volume.

# Dockerfiles

## Dockerfile.jupyter

This Dockerfile sets up a Jupyter environment based on the `jupyter/scipy-notebook` image. It exposes port 8888 and sets the working directory to `/app`. The command `start-notebook.sh` is used to start the Jupyter Notebook server.

## Dockerfile.libraries

This Dockerfile sets up a Python environment based on the `python:3` image. It installs the Python libraries listed in the `requirements.txt` file into a specified directory `/libraries`.

## Customization

* **Python Libraries**: Modify the `requirements.txt` file to include any additional Python libraries you require.
* **Jupyter Configuration**: Adjust the Jupyter configuration in the `Dockerfile.jupyter` file as needed.