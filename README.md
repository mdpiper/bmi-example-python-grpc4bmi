# bmi-example-python-grpc4bmi

Set up a [grpc4bmi](https://grpc4bmi.readthedocs.io) server
to run a containerized version
of the [Basic Model Interface](https://bmi.readthedocs.io)
[Python example](https://github.com/csdms/bmi-example-python).

## Build

Build this example locally with:
```
docker build --tag bmi-example-python-grpc4bmi .
```
The image is built on the [mdpiper/bmi-example-python](https://hub.docker.com/r/mdpiper/bmi-example-python) base image.
The OS is Linux/Ubuntu.
`conda` and `mamba` are installed in `opt/conda`.
The *base* environment is activated,
and the Python BMI example is installed into it.

## Run

Use the grpc4bmi [Docker client](https://grpc4bmi.readthedocs.io/en/latest/container/usage.html#docker)
to access the BMI methods of the containerized model.
For example, in a Python session, try:
```python
from grpc4bmi.bmi_client_docker import BmiClientDocker


m = BmiClientDocker(image='mdpiper/bmi-example-python-grpc4bmi', image_port=55555, work_dir=".")
m.get_component_name()

del m  # needed to stop container
```

The container is pulled from Docker Hub.

## Developer notes

A versioned image built from this repository is hosted on Docker Hub
at [mdpiper/bmi-example-python-grpc4bmi](https://hub.docker.com/r/mdpiper/bmi-example-python-grpc4bmi).
To tag, build, and push an update, run:
```
docker build --tag mdpiper/bmi-example-python-grpc4bmi:tagname .
docker push mdpiper/bmi-example-python-grpc4bmi:tagname
```
where `tagname` is, e.g., `0.1` or `latest`.

A user can pull this image from Docker Hub with:
```
docker pull mdpiper/bmi-example-python-grpc4bmi
```
