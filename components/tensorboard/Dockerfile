FROM tensorflow/tensorflow:2.3.1

RUN pip install --upgrade pip

COPY ./requirements.txt .
RUN pip install -r requirements.txt && rm ./requirements.txt
