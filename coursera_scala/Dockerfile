FROM openjdk:8-jdk

### Install coursera requirements

RUN apt-get update && \
	apt-get install -y apt-transport-https

RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list && \
	apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823 && \
  apt-get update && \
	apt-get install -y sbt

ADD example_build /example_build

### build sbt/scala env
RUN cd /example_build && sbt about

### Taken from fdm1/base_dev (tweak to libjpeg to get to work)

RUN apt-get update && apt-get install --fix-missing -y build-essential \
                          vim \
                          vim-nox \
                          tmux \
                          git \
                          rake \
                          curl \
                          ruby-dev \
                          libpng-dev \
                          libjpeg62-turbo-dev \
                          libfreetype6-dev \
                          libxft-dev \
                          man

# ### install rvm needed for command-t in vim_dotfiles
RUN curl -sSL https://rvm.io/mpapis.asc | gpg --import - && \
      curl -L https://get.rvm.io | bash -s stable && \
      /bin/bash -l -c "rvm requirements" && \
      /bin/bash -l -c "rvm install 2.1.1"


### vim config setup
RUN git clone https://github.com/braintreeps/vim_dotfiles.git && \
  cd vim_dotfiles && \
  rake && \
  cd ~/.vim/plugged/command-t/ruby/command-t && \
  /bin/bash -l -c "rvm use system" && \
  ruby extconf.rb && \
  make

RUN git clone https://github.com/fdm1/frank_dotfiles && \
  cd frank_dotfiles && \
  rake



CMD bash
