#
# React
# Nodejs 10.15.1
#
#
FROM tama8/centos6-anyenv
MAINTAINER tamashiro

#RUN curl -L -O http://ftp.riken.jp/Linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm && \
#    rpm -Uhv epel-release-6-8.noarch.rpm
#
#RUN yum install -y --enablerepo=epel re2c && \
#    yum clean all
#
#RUN yum install -y libtidy-devel gcc-c++ libicu-devel libxml2-devel libxslt-devel libcurl-devel libpng-devel libicu-devel libjpeg-devel libpng-devel bison-devel && \
#    yum clean all


# node
USER dev
RUN $HOME/.anyenv/bin/anyenv install nodenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv install 10.15.1'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv global 10.15.1'
RUN /bin/bash -l -c 'npm install -g create-react-app'


EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
