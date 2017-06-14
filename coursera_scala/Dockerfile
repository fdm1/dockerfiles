FROM williamyeh/scala:2.11.6 


### Install coursera requirements

RUN apt-get update && \
	apt-get install -y apt-transport-https 

RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list && \
	apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823 && \
	apt-get update && \
	apt-get install -y sbt

RUN sbt about



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

# Set locale for vim to work correctly
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
	locale-gen en_US.UTF-8 && \
      locale -a && \
      echo '[[ $TMUX = "" ]] && export TERM="xterm-256color"' >> ~/.bashrc

# install rvm needed for command-t in vim_dotfiles
RUN curl -sSL https://rvm.io/mpapis.asc | gpg --import - && \
      curl -L https://get.rvm.io | bash -s stable && \
      /bin/bash -l -c "rvm requirements" && \
      /bin/bash -l -c "rvm install 2.1.1"

### Fix for Debian locale

# RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
#        locale-gen "en_US.UTF-8 UTF-8"


# vim config setup
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

RUN     echo "export LC_CTYPE=en_US.UTF-8" >> ~/.bashrc && \
     echo "export LC_ALL=en_US.UTF-8" >> ~/.bashrc 

RUN sbt

CMD bash
