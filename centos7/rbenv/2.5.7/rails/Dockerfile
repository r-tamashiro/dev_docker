#
# Centos7
# ruby 2.5.7（AppEngine）
# Ruby on Rails 6.0.1
#  DB: MySQL
# NodeJS 10.15.1
# yarn 1.19.1
#
FROM tama8/centos7-rbenv:2.5.7
MAINTAINER tamashiro

RUN yum install -y mariadb-devel && \
    yum clean all

# Rails
USER dev
RUN /bin/bash -l -c 'gem install rails -v 6.0.1'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'rbenv global 2.5.7'
RUN /bin/bash -l -c 'gem install mysql2'

# node
USER dev
RUN $HOME/.anyenv/bin/anyenv install nodenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'touch $(nodenv root)/default-packages'
RUN /bin/bash -l -c 'nodenv install 10.15.1'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv global 10.15.1'
RUN /bin/bash -l -c 'npm install -g yarn@1.19.1'
RUN echo 'export NODE_PATH=$(npm root -g)' >> ~/.bashrc


EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
