[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/hZT7Ifs6)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=12349273&assignment_repo_type=AssignmentRepo)
# Regression Model

Building and deploying a regression ML model.

This code is used in this [blog post](https://www.tekhnoal.com/regression-model.html).

## Requirements

Python 3.9

## Installation 

The Makefile included with this project contains targets that help to automate several tasks.

To download the source code execute this command:

```bash
git clone https://github.com/schmidtbri/regression-model
```

Then create a virtual environment and activate it:

```bash
# go into the project directory
cd regression-model

 #Installing virtualenv 
    py -m pip install --user virtualenv
# creating a virtualenv in you project folder
  py -m venv env
#activate the env
  .\env\Scripts\activate


source venv/bin/activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

The requirements.txt file only includes the dependencies needed to make predictions with the model. To train the model you'll need to install the dependencies from the train_requirements.txt file:

```bash
make train-dependencies
```

## Running the Unit Tests
To run the unit test suite execute these commands:
 
```bash
# first install the test dependencies
make test-dependencies
pip install -r test_requiremnet.txt

# run the test suite
make test-dependencies
pipenv install test_requiremnet



# run the test suite
rename test files they should start with 'test': test_transformers.py and test_ model.py
run the test with command:
                        python -m unittest
the result is this:
"Ran 5 tests in 0.990s
OK"

make test

# clean up the unit tests
make clean-test
```
![Test running resualt](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/4ca3adb031dcbd45000a5acaabb1f427305b3c56/images/run%205%20test%20ok.png)
## Running the Service

To start the service locally, execute these commands:

```bash
uvicorn rest_model_service.main:app --reload
```
![running service](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/4ca3adb031dcbd45000a5acaabb1f427305b3c56/images/running%20the%20service.png)
## Generating an OpenAPI Specification

To generate the OpenAPI spec file for the REST service that hosts the model, execute these commands:

```bash
export PYTHONPATH=./
generate_openapi --output_file=service_contract.yaml
```
for undrestanding how the data prepared and how modwl work visite blog https://www.tekhnoal.com/regression-model.html

install anoconda
'''bash 
install anaconda on your system
open anaconda promot and type command:
conda install ipykernel 
you can run jupyter files at vscode
'''

run commands at file: data_exploration.ipynp
'''bash
create data folder at main directory
download the insurance.csv file and past it hear 
run the command one by one
'''
![run data_exploration](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/ccaebd4c954a73b2427e52218bc9cdda6298853b/images/run%20data_exploration.png)

run data_preparation.ipynb 
'''bash
at file data_preparation.ipynb run all the commands and finally create transformer.joblib file
'''
![run dataprepration file](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/b1997f68f26f083e3db63139b9ba0a665d194c03/images/data_preparation.png)
run model_traning.ipynb file
'''bash
run all commands at model_traning file.
it create a model.joblib file
'''
![runmodeltraning file](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/d0dcdc48fe2734551ced38f48c8251802b63b0eb/images/model%20traning.png)

run atmodel_validation.ipynb file
'''bash
run all commands atmodel_validation file.
it validate the model and you can see the result at tow graphe
Residuals plot
Prediction Error Plot
'''
![Residuals plot](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/d0dcdc48fe2734551ced38f48c8251802b63b0eb/images/Generate%20Residuals%20Plot.png)

![Prediction Error Plot](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/d0dcdc48fe2734551ced38f48c8251802b63b0eb/images/Generate%20Prediction%20Error%20Plot.png)
To stop the docker image, execute this command:


## Docker

To build a docker image for the service, run this command:

```bash
docker build -t insurance_charges_model:0.1.0 .
```

To run the image, execute this command:

```bash
docker run -d -p 80:80 insurance_charges_model:0.1.0
```
![run docker image](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/6a8d24b8f6ebfaad8e699f93c5bf85ff76b4ff13/images/create%20and%20run%20docker%20image.png)
To watch the logs coming from the image, execute this command:

```bash
docker logs $(docker ps -lq)
```
![docker_log](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/4c2d1b85e63610aabdf3020f4152fcd41c03a1dc/images/docker_log.png)


view the model API homepage
```bash
to run the Model's API at your browser's address bar type:
http://localhost
```
![model api](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/62ea51af71bf13dfa6634f7e5f308d01d30645b7/images/model_api.png)

Seeing the information about Model (Sending get request):
```bash
you can get information about model by sending get request to this address:
http://localhost/api/models
```
you can sent get request from your browsers (typing the address at your browser) or from other softwares like insomnia 
![get request](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/413177d039ad031acb7339b855732bf954e78bee/images/get%20request.png)

Send the information for model ang get the charges result (Sending post request): 
```bash
you can sent post request to model from insomnia software:
at address bar select POST method and enter the url address: http://localhost/api/models/insurance_charges_model/prediction
at JSON enter data as a dictianary like this:
{
  "age": 38,
  "sex": "male",
  "bmi": 50,
  "children": 1,
  "smoker": false,
  "region": "southwest"
}
when you send the request you can see the result at preview part of the software like this:
{
	"charges": 7806.01
}
```
![post request](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/6a75ccfb61406d3a079ffacee31d698d1521534e/images/post%20request.png)

# Adding Logging feature
for add logging feature to the model we can use Logging for ML Model Deployments from https://github.com/schmidtbri/logging-for-ml-models and integrate it at our model.

1. To download the source code execute this command:
'''bash
git clone https://github.com/schmidtbri/logging-for-ml-models
'''
the logging for ML Models was written for another model (risk model) but we want to use this service in our model so we do not need all of the codes. 
2. we should select part of it and move them to our project:
list of files and folder that we need:
'''bash
configuration folder
ml_model_logging folder
model_service.yaml file from kubernetes folder
'''
copy these folders and file and paste them at our model main directory (we past the model_service.yaml file at kubernetes folder)

3. change the dockerfile at our model and write the code bellow on it:
'''bashh
FROM tiangolo/uvicorn-gunicorn-fastapi:python3.9 as base

# creating and activating a virtual environment
ENV VIRTUAL_ENV=/opt/venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# installing dependencies
COPY ./service_requirements.txt ./service_requirements.txt
RUN pip install --no-cache -r service_requirements.txt

FROM base as runtime

ARG DATE_CREATED
ARG REVISION
ARG VERSION

LABEL org.opencontainers.image.title="Logging for ML Models"
LABEL org.opencontainers.image.description="Logging for machine learning models."
LABEL org.opencontainers.image.created=$DATE_CREATED
LABEL org.opencontainers.image.authors="6666331+schmidtbri@users.noreply.github.com"
LABEL org.opencontainers.image.source="https://github.com/schmidtbri/logging-for-ml-models"
LABEL org.opencontainers.image.version=$VERSION
LABEL org.opencontainers.image.revision=$REVISION
LABEL org.opencontainers.image.licenses="MIT License"
LABEL org.opencontainers.image.base.name="python:3.9-slim"

WORKDIR /service

#copy Files
COPY ./insurance_charges_model ./insurance_charges_model
COPY ./rest_config.yaml ./rest_config.yaml
COPY ./service_requirements.txt ./service_requirements.txt
COPY ./kubernetes_rest_config.yaml ./kubernetes_rest_config.yaml
COPY ./configuration ./configuration

# Expose the port your application runs on
EXPOSE 8000

# install packages


RUN apt-get update -y && \
    apt-get install -y --no-install-recommends libgomp1 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*


COPY --from=base /opt/venv ./venv

COPY ./ml_model_logging ./ml_model_logging
COPY ./LICENSE ./LICENSE

ENV PATH /service/venv/bin:$PATH
ENV PYTHONPATH="${PYTHONPATH}:/service"

ENV APP_MODULE=rest_model_service.main:app
CMD ["uvicorn", "rest_model_service.main:app", "--host", "0.0.0.0", "--port", "8000"]
'''
4. chang the rest_config.yaml file like code below:

```bash
service_title: Insurance Charges Model Service
models:
  - class_path: insurance_charges_model.prediction.model.InsuranceChargesModel
    create_endpoint: true
    decorators:
      - class_path: ml_model_logging.logging_decorator.LoggingDecorator
        configuration:
          input_fields: ["age", "sex"]
          output_fields: ["charges"]
logging:
    version: 1
    disable_existing_loggers: false
    formatters:
      json_formatter:
        class: pythonjsonlogger.jsonlogger.JsonFormatter
        format: "%(asctime)s %(node_ip)s %(name)s %(levelname)s %(message)s"
    filters:
      environment_info_filter:
        "()": ml_model_logging.filters.EnvironmentInfoFilter
        env_variables:
        - NODE_IP
    handlers:
      stdout:
        level: INFO
        class: logging.StreamHandler
        stream: ext://sys.stdout
        formatter: json_formatter
        filters:
        - environment_info_filter
    loggers:
      root:
        level: INFO
        handlers:
        - stdout
        propagate: true

```
5. at configuration folder change the kubernetes_rest_config.yaml file:
'''bash
service_title: Insurance Charges Model Service
models:
  - class_path: insurance_charges_model.prediction.model.InsuranceChargesModel
    create_endpoint: true
    decorators:
      - class_path: ml_model_logging.logging_decorator.LoggingDecorator
        configuration:
          input_fields: ["age", "sex"]
          output_fields: ["charges"]
logging:
    version: 1
    disable_existing_loggers: false
    formatters:
      json_formatter:
        class: pythonjsonlogger.jsonlogger.JsonFormatter
        format: "%(asctime)s %(pod_name)s %(node_name)s %(app_name)s %(name)s %(levelname)s %(message)s"
    filters:
      environment_info_filter:
        "()": ml_model_logging.filters.EnvironmentInfoFilter
        env_variables:
        - POD_NAME
        - NODE_NAME
        - APP_NAME
    handlers:
      stdout:
        level: INFO
        class: logging.StreamHandler
        stream: ext://sys.stdout
        formatter: json_formatter
        filters:
        - environment_info_filter
    loggers:
      root:
        level: INFO
        handlers:
        - stdout
        propagate: true
'''
6. at configuration folder change the rest_configuration.yaml file:
'''bash
service_title: Insurance Charges Model Service
models:
  - class_path: insurance_charges_model.prediction.model.InsuranceChargesModel
    create_endpoint: true
    decorators:
      - class_path: ml_model_logging.logging_decorator.LoggingDecorator
        configuration:
          input_fields: ["age", "sex"]
          output_fields: ["charges"]
logging:
    version: 1
    disable_existing_loggers: false
    formatters:
      json_formatter:
        class: pythonjsonlogger.jsonlogger.JsonFormatter
        format: "%(asctime)s %(node_ip)s %(name)s %(levelname)s %(message)s"
    filters:
      environment_info_filter:
        "()": ml_model_logging.filters.EnvironmentInfoFilter
        env_variables:
        - NODE_IP
    handlers:
      stdout:
        level: INFO
        class: logging.StreamHandler
        stream: ext://sys.stdout
        formatter: json_formatter
        filters:
        - environment_info_filter
    loggers:
      root:
        level: INFO
        handlers:
        - stdout
        propagate: true
'''
7. we can delete the files service.yaml, namespace.yaml, deployment.yaml files from kubernetes

8. add 'python-json-logger==2.0.7' to service_requirements.txt file

# Deploying the Model
## Creating a Docker Image

 now we can create our docker image with command below:
'''bash
docker build --build-arg DATE_CREATED="$DATE_CREATED" --build-arg VERSION="0.1.0" --build-arg REVISION="$REVISION" -t insurance_charges_model_service:0.1.0 .
'''
we can run our image with command below:
'''bash
docker run -d -p 8000:8000 -e REST_CONFIG=./configuration/rest_configuration.yaml -e NODE_IP="145.156.147.168" --name insurance_charges_docker insurance_charges_model_service:0.1.0
'''
now you can see our model at your browser with address:
'''bash
http://localhost:8000

'''
![homepage](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/6a75ccfb61406d3a079ffacee31d698d1521534e/images/homepage.png)

if you send the post request like this:
![post request](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/6a75ccfb61406d3a079ffacee31d698d1521534e/images/post%20request.png)

you can see the log at your docker image: 
![post request](https://github.com/uqam-lomagnin/logging-of-regression-model-pedram6403/blob/6a75ccfb61406d3a079ffacee31d698d1521534e/images/dockerlogforpost.png)

```bash
docker kill $(docker ps -lq)
```
