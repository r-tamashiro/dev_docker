#
# PHP 7,2
# Nodejs 10.15.1
#
#
FROM tama8/centos6-anyenv
MAINTAINER tamashiro

# go
USER dev
RUN $HOME/.anyenv/bin/anyenv install goenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'goenv install 1.12.0'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'goenv global 1.12.0'
RUN echo 'export GOPATH="$HOME/go"' >> ~/.bashrc
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'go get -u github.com/golang/dep/cmd/dep'
RUN /bin/bash -l -c 'export PATH="$HOME/go/1.12.0/bin:$PATH"'




EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
