# ML Platform

reference: https://github.com/erdiolmezogullari/ml-fmnist-mlflow-tensorboard

In this case, we used docker container technologies to create the ML platform from scratch.
It consists of four different docker containers (MLflow, JupyterLab, PostgreSQL, TensorBoard) that are already built in `docker-compose.yml`.

## Example Project Structure

```
.
├── README.md
├── app
│   ├── cifar10.ipynb
│   └── train-cifar10.py
├── artifacts
├── components
│   ├── jupyterlab
│   ├── mlflow
│   ├── postgres
│   └── tensorboard
├── data
├── docker-compose.yml
├── logs
│   ├── postgres_storage
│   └── tensorboard
├── makefile
├── platform.sh
└── platform_env.sh
```

## Prerequisites

- Install Docker
- Install docker-compose

## Usage

1. Add the training data under the `data` directory.
2. Add training scripts, notebooks under the `app` directory.
3. Experiment artifacts would be stored under the `artifacts` directory.
4. Database logs and Tensorboard logs would be stored under the `logs` directory.
5. You will find `makefile` to kick off the platform. It has three different commands to build, start, and stop platform.

* To build platform

        make build
    
* To start platform

        make up
    
* To stop platform

        make down
        
* To visit JupyterLab type the following address on your favorite browser:
        
        http://localhost:8888/

* To visit TensorBoard type the following address on your favorite browser:
    
        http://localhost:6006/
     
* To visit Mlflow type the following address on your favorite browser:
    
        http://localhost:5000/
