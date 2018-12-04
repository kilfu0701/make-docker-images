FROM alpine:3.8
LABEL Maintainer="BoRu Su <kilfu0701@gmail.com>"

RUN apk add --update alpine-sdk
RUN apk add --no-cache gcc g++ libxml2 libxml2-dev libxslt-dev
RUN apk add --no-cache python3 python3-dev && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --upgrade pip setuptools && \
    if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi && \
    if [[ ! -e /usr/bin/python ]]; then ln -sf /usr/bin/python3 /usr/bin/python; fi && \
    rm -r /root/.cache

RUN pip install lxml==4.2.5

RUN pip install \
    numpy==1.15.4 \
    pandas==0.23.4 \
    pyCx==0.0.6 \
    python-dateutil==2.7.5 \
    pytz==2018.7 \
    PyYAML==3.13 \
    six==1.11.0 \
    SQLAlchemy==1.2.14

#ENTRYPOINT ["/bin/sh"]
