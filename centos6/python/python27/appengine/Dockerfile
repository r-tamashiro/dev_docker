#
# anyenv
# pyenv
# Python 2.7.15
# Nodejs 10.15.1
#
FROM tama8/centos6-anyenv
MAINTAINER tamashiro

USER dev
RUN $HOME/.anyenv/bin/anyenv install pyenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'pyenv install 2.7.15'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'pyenv global 2.7.15'

USER root
# Google App Engine SDK
RUN curl -O  https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.38.zip && \
  unzip google_appengine_1.9.38.zip -d /usr/local/ && \
  rm google_appengine_1.9.38.zip

# modify gae scripts
RUN sed -i -e "s/\/usr\/bin\/env *python/\/usr\/bin\/env python2.7/" /usr/local/google_appengine/*.py


# node
USER dev
RUN $HOME/.anyenv/bin/anyenv install nodenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv install 10.15.1'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv global 10.15.1'

EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
