# BentoML - classification model
BentoML classification model train, test and build


## Install

```bash
pip install -r ./requirements.txt
```


## Train
```bash
python ./train.py
```

## Run the service

```bash
bentoml serve service.py:svc
```

## Send test request

Test the `/predict` endpoint with expected input:

```bash
$ curl -X POST -H "content-type: application/json" --data '{"sepal_len": 7.2, "sepal_width": 3.2, "petal_len": 5.2, "petal_width": 2.2}' http://127.0.0.1:3000/classify
```

Test sending request with optional field:
```bash
$ curl -X POST -H "content-type: application/json" --data '{"sepal_len": 7.2, "sepal_width": 3.2, "petal_len": 5.2, "petal_width": 2.2, "request_id": 123}' http://127.0.0.1:3000/classify
```

Test sending request with wrong field name:

```bash
$ curl -X POST -H "content-type: application/json" --data '{"sepal_len": 6.2, "sepal_width": 3.2, "petal_len": 5.2, "petal_width_typo": 2.2}' http://127.0.0.1:3000/classify

"BentoService error handling API request: Invalid JSON input received: 2 validation errors for IrisFeatures
  petal_width
    field required (type=value_error.missing)
  petal_width_typo
    extra fields not permitted (type=value_error.extra)"%
```


## Build Bento

```
bentoml build
```

## Build docker image

```
bentoml containerize iris_classifier_pydantic:latest
```
