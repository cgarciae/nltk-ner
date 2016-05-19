FROM python:3.5

RUN echo "deb http://ftp.de.debian.org/debian jessie-backports main" >> /etc/apt/sources.list && \
  apt-get update && apt-get -y install \
	openjdk-8-jdk \
	openjdk-8-jre \
	unzip \
	wget


ENV NER_VERSION_DATE 2015-12-09
ENV SPANISH_VERSION_DATE 2015-10-14


RUN mkdir /ner && \
  cd /ner && \
  export NER_URL="http://nlp.stanford.edu/software/stanford-ner-${NER_VERSION_DATE}.zip" && \
  export SPA_URL="http://nlp.stanford.edu/software/stanford-spanish-corenlp-${SPANISH_VERSION_DATE}-models.jar" && \
  wget -O ner.zip ${NER_URL} && \
  unzip ner.zip && \
  mv stanford-ner-${NER_VERSION_DATE}/* . && \
  rm -fr stanford-ner-${NER_VERSION_DATE}/ && \
  rm ner.zip && \
  wget -O spa.zip ${SPA_URL} && \
  unzip spa.zip -d stanford-spanish && \
  mv stanford-spanish/edu/stanford/nlp/models/ner/* classifiers/  && \
  rm -fr stanford-spanish && \
  rm spa.zip

RUN pip install nltk

ENV CLASSPATH /ner
ENV STANFORD_MODELS /ner/classifiers
ENV NER_VERSION_NUMBER 3.6.0

RUN mv /ner/stanford-ner-${NER_VERSION_NUMBER}.jar /ner/stanford-ner.jar
