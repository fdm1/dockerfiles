TAG = fdm1/spark:2.1.1

build:
		docker build --pull -t $(TAG) .

push: build
		docker push $(TAG)

interactive:
		docker run -it $(TAG) /bin/bash

all: build

