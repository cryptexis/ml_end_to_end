FROM python:3

RUN pip install flask

ADD app.py app.py
EXPOSE 5000
ENTRYPOINT ["python", "app.py"]