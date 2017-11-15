TAG = fdm1/spark-scala-sbt

build:
		docker build --pull -t $(TAG) .

push: build
		docker push $(TAG)

interactive:
		docker run -it $(TAG) --rm /bin/bash

all: build
