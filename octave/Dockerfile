FROM debian:wheezy 

RUN apt-get update
RUN apt-get install -y octave
RUN apt-get autoclean

VOLUME ["/source"]
WORKDIR /source
CMD ["octave"]
