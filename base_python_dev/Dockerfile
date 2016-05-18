FROM fdm1/base_dev:python3

RUN apt-get update && apt-get install --fix-missing -y python3 \
                          python3-dev \
                          python3-pip \
                          python-setuptools

RUN pip3 install pandas \
                 ipython \
                 jupyter \
                 ipykernel \
                 matplotlib

EXPOSE 8888

CMD bash

