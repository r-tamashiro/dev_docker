#
# Centos7
# Nodejs 10.15.1
# Monaca CLI
#
FROM tama8/centos7-anyenv
MAINTAINER tamashiro

COPY jdk-8u211-linux-x64.rpm /tmp/
RUN rpm -Uhv /tmp/jdk-8u211-linux-x64.rpm


# node
USER dev
RUN $HOME/.anyenv/bin/anyenv install nodenv
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv install 10.15.1'
RUN /bin/bash -l -c 'exec $SHELL -l'
RUN /bin/bash -l -c 'nodenv global 10.15.1'
RUN /bin/bash -l -c 'npm install -g monaca'

# Android SDK
RUN mkdir $HOME/android-sdk && curl -L -o $HOME/android-sdk/tools.zip https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip && \
  unzip $HOME/android-sdk/tools.zip -d $HOME/android-sdk
RUN echo 'export ANDROID_HOME="$HOME/android-sdk"' >> ~/.bashrc
RUN /bin/bash -l -c 'yes | $ANDROID_HOME/tools/bin/sdkmanager --licenses'
RUN /bin/bash -l -c '$ANDROID_HOME/tools/bin/sdkmanager "build-tools;19.1.0"'

# Gradle
RUN curl -L -o $HOME/gradle.zip https://services.gradle.org/distributions/gradle-2.14-all.zip && \
  unzip $HOME/gradle.zip -d $HOME
RUN echo 'export GRADLE_HOME="$HOME/gradle-2.14"' >> ~/.bashrc
RUN echo 'export PATH="$GRADLE_HOME/bin:$PATH"' >> ~/.bashrc

# Glibc 2.14



EXPOSE 22

USER root
CMD ["/usr/sbin/sshd","-D"]
