# nltk + ner + docker
Docker image based on `python:3.5` with JDK 8 and nltk installed.

### Usage
NER gets installed `/ner`. The NER `.jar` get renamed to `stanford-ner.jar` to comply with how `nltk` searches for this file.

#### Enviroment Variables
This image exposes/sets the following enviroment variables.

```
ENV NER_VERSION_DATE 2015-12-09
ENV SPANISH_VERSION_DATE 2015-10-14
ENV NER_VERSION_NUMBER 3.6.0

ENV CLASSPATH /ner
ENV STANFORD_MODELS /ner/classifiers
```
