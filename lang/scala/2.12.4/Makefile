TAG = fdm1/scala:2.12.4

BASE_DIR := $(dir $(abspath $(lastword $(MAKEFILE_LIST))))

build:
		cd $(BASE_DIR) && \
		docker build \
			--file $(BASE_DIR)/Dockerfile \
			--pull \
			--tag $(TAG) \
		 	.

push: build
		docker push $(TAG)

interactive:
		docker run -it $(TAG) /bin/bash

all: build

