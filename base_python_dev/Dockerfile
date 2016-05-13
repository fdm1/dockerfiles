FROM ubuntu:14.04

RUN apt-get update && apt-get install --fix-missing -y build-essential \
                          vim \
                          vim-nox \
                          tmux \
                          git \
                          rake \
                          curl \
                          ruby-dev \
                          python \
                          python-dev \
                          python3-dev \
                          python-pip \
                          python3-pip \
                          python-setuptools \
                          libpng-dev \
                          libjpeg8-dev \
                          libfreetype6-dev

RUN pip install pandas \
                ipython \
                jupyter \ 
                matplotlib

RUN pip3 install pandas \
                 ipython \
                 ipykernel \
                 matplotlib

RUN ipython3 kernel install

# Set locale for vim to work correctly
RUN locale-gen en_US.UTF-8 && \
      locale -a && \
      echo "export LC_CTYPE=en_US.UTF-8" >> ~/.bashrc && \
      echo "export LC_ALL=en_US.UTF-8" >> ~/.bashrc && \
      echo '[[ $TMUX = "" ]] && export TERM="xterm-256color"' >> ~/.bashrc

# install rvm needed for command-t in vim_dotfiles
RUN curl -sSL https://rvm.io/mpapis.asc | gpg --import - && \
      curl -L https://get.rvm.io | bash -s stable && \
      /bin/bash -l -c "rvm requirements" && \
      /bin/bash -l -c "rvm install 2.1.1"

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


EXPOSE 8888

CMD bash

