FROM python:alpine

COPY . /opt/taxii
COPY ./docker_utils/*.json /opt/taxii
VOLUME /config
WORKDIR /opt/taxii
RUN pip install --upgrade pip setuptools \
    && pip install pymongo \
    && pip install .
