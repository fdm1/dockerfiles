TAG = fdm1/scala:2.11.7

build:
		docker build --pull -t $(TAG) .

push: build
		docker push $(TAG)

interactive:
		docker run -it $(TAG) /bin/bash

all: build

