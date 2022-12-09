## Running without Docker

First let's look into the code

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return "Hello World!"

app.run(host='0.0.0.0', port=5000)
```

And now let's run it on our machine
```bash
pip install -r requirements.txt 
```

```bash
python app.py
```

Open in the browser

```bash
http://localhost:5000/
```

## Looking into Docker contents


```docker
FROM python:3

RUN pip install flask

ADD app.py app.py
EXPOSE 5000
ENTRYPOINT ["python", "app.py"]
```

## Building Docker Image

```bash
docker build -t <username>/mle2e_docker_intro .
```

Listing docker images
```
docker images
```

## Running Docker Image

Without port mapping & name & automatic cleaning
```
docker run <username>/mle2e_docker_intro
```


Without name & automatic cleaning
```
docker run -p 8888:5000 <username>/mle2e_docker_intro
```

Without automatic cleaning
```
docker run -p 8888:5000 --name bananas <username>/mle2e_docker_intro
```

```
docker run --rm -p 8888:5000 --name bananas <username>/mle2e_docker_intro
```

Accessing in the browser

```
http://localhost:8888/
```

## Stop the container

```
docker stop bananas
```