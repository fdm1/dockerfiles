TAG = fdm1/zeppelin:0.7.2

build:
		docker build --pull -t $(TAG) .

push: build
		docker push $(TAG)

interactive:
		docker run -it $(TAG) /bin/bash

all: build

