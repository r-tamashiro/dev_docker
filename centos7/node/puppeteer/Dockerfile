#
# Centos7
# Nodejs 10.15.1
# puppeteer 1.11.0
#
FROM tama8/centos7-anyenv
MAINTAINER tamashiro


RUN yum install -y libX11 libXcomposite libXcursor libXdamage libXext libXi libXtst cups-libs libXScrnSaver libXrandr alsa-lib pango atk at-spi2-atk gtk3 && \
    yum clean all

# 文字化け対策
RUN yum  install -y ipa-gothic-fonts xorg-x11-fonts-100dpi xorg-x11-fonts-75dpi xorg-x11-utils xorg-x11-fonts-cyrillic xorg-x11-fonts-Type1 xorg-x11-fonts-misc && \
    yum clean all

# node
USER dev
RUN $HOME/.anyenv/bin/anyenv install nodenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv install 10.15.1'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv global 10.15.1'
RUN /bin/bash -l -c 'npm install -g puppeteer@1.11.0'
RUN echo 'export NODE_PATH=$(npm root -g)' >> ~/.bashrc


EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
