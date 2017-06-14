FROM ubuntu:14.04

RUN apt-get update
RUN apt-get install -y build-essential vim vim-nox tmux git rake curl ruby-dev
RUN apt-get install -y python python-dev python-setuptools
RUN easy_install pip

# install early for base-package
RUN pip install pandas

# Set locale for vim to work correctly
RUN locale-gen en_US.UTF-8 && locale -a && echo "export LC_CTYPE=en_US.UTF-8" >> ~/.bashrc && echo "export LC_ALL=en_US.UTF-8" >> ~/.bashrc

# install rvm needed for command-t in vim_dotfiles
RUN curl -sSL https://rvm.io/mpapis.asc | gpg --import -
RUN curl -L https://get.rvm.io | bash -s stable
RUN /bin/bash -l -c "rvm requirements"
RUN /bin/bash -l -c "rvm install 2.1.1"

# vim config setup
RUN git clone https://github.com/braintreeps/vim_dotfiles.git 
RUN cd vim_dotfiles && rake
RUN cd ~/.vim/plugged/command-t/ruby/command-t && /bin/bash -l -c "rvm use system" && ruby extconf.rb && make

RUN git clone https://github.com/fdm1/frank_dotfiles && cd frank_dotfiles && rake

# project-specific packages
RUN pip install ipython
RUN pip install googlefinance
RUN pip install pandas_datareader


CMD python

