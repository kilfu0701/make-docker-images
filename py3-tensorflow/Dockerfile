FROM ubuntu:18.04
LABEL Maintainer="BoRu Su <kilfu0701@gmail.com>"

RUN apt-get update \
  && apt-get install -y python3-pip python3-dev \
  && cd /usr/local/bin \
  && ln -s /usr/bin/python3 python \
  && pip3 install --upgrade pip

RUN pip install Django==2.1.2 pandas numpy bs4 pyyaml tensorflow

ENTRYPOINT ["python3"]
