#
# 2019/06/03
#   CentOS 7 + epel,remi,rpmforge
#	anyenv
#

FROM centos:7
MAINTAINER tamashiro

# update yum
RUN yum update -y && \
    yum clean all

RUN yum install -y git gcc make openssh-server openssh-clients sudo tar unzip which && \
    yum clean all

## libraries
RUN yum install -y bzip2-devel zlib-devel openssl-devel sqlite-devel ncurses-devel readline-devel tk-devel && \
    yum clean all

# initialize for ssh
RUN sed -i '/pam_loginuid\.so/s/required/optional/' /etc/pam.d/sshd

# create login user
RUN useradd -d /home/dev -m -s /bin/bash dev
RUN echo dev:dev | chpasswd
RUN echo 'dev ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# 使わないにしてもここに公開鍵を登録しておかないとログインできない
RUN ssh-keygen -t rsa -N "" -f /etc/ssh/ssh_host_rsa_key

# timezone
RUN cp -p /usr/share/zoneinfo/Japan /etc/localtime

USER dev
RUN git clone https://github.com/riywo/anyenv ~/.anyenv

RUN mkdir -p $HOME/.anyenv/plugins
RUN git clone https://github.com/znz/anyenv-update.git $HOME/.anyenv/plugins/anyenv-update

RUN echo 'export PATH="$HOME/.anyenv/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(anyenv init -)"' >> ~/.bashrc
RUN exec $SHELL -l
RUN $HOME/.anyenv/bin/anyenv install --force-init


EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
