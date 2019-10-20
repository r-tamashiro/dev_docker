#
# Centos7
# ruby 2.6.5
#
FROM tama8/centos7-anyenv
MAINTAINER tamashiro

RUN yum install -y bzip2 && \
    yum clean all

#RUN yum install -y libX11 libXcomposite libXcursor libXdamage libXext libXi libXtst cups-libs libXScrnSaver libXrandr alsa-lib pango atk at-spi2-atk gtk3 && \
#    yum clean all
#
## 文字化け対策
#RUN yum  install -y ipa-gothic-fonts xorg-x11-fonts-100dpi xorg-x11-fonts-75dpi xorg-x11-utils xorg-x11-fonts-cyrillic xorg-x11-fonts-Type1 xorg-x11-fonts-misc && \
#    yum clean all
#
## ruby
USER dev
RUN $HOME/.anyenv/bin/anyenv install rbenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'cd $(rbenv root g)/plugins/ruby-build && git pull'
RUN /bin/bash -l -c 'rbenv install 2.6.5'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'rbenv global 2.6.5'


EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
