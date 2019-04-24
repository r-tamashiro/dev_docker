#
# anyenv
# pyenv
# Python 2.7.15
#
FROM tama8/centos6-anyenv
MAINTAINER tamashiro

USER dev
RUN $HOME/.anyenv/bin/anyenv install pyenv
RUN exec $SHELL -l
RUN source ~/.bashrc && \
  pyenv install 2.7.15 && \
  exec $SHELL -l && \
  pyenv global 2.7.15

USER root
# Google App Engine SDK
RUN curl -O  https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.38.zip && \
  unzip google_appengine_1.9.38.zip -d /usr/local/ && \
  rm google_appengine_1.9.38.zip

# modify gae scripts
RUN sed -i -e "s/\/usr\/bin\/env *python/\/usr\/bin\/env python2.7/" /usr/local/google_appengine/*.py
