FROM fdm1/base_dev

RUN apt-get update && apt-get install --fix-missing -y python \
                          python-dev \
                          python-pip \
                          python-setuptools

RUN pip install pandas \
                 ipython \
                 jupyter \
                 ipykernel \
                 matplotlib

EXPOSE 8888

CMD bash

