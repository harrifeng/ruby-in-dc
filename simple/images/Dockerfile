# image name: harrifeng/simple
FROM ubuntu:16.04
RUN apt-get update && \
DEBIAN_FRONTEND=noninteractive apt-get -y install \
gcc \
make \
libssl-dev \
libreadline-dev \
zlib1g-dev \
libsqlite3-dev \
curl \
silversearcher-ag \
tmux \
emacs \
git \
net-tools \
iputils-ping \
python \
python-pip \
sudo \
wget \
sqlite3 \
openssh-server

# For nodejs
RUN curl -sL https://deb.nodesource.com/setup_4.x | bash -
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install nodejs
RUN npm install -g js-beautify webpack tern
RUN npm install -g bower ember-cli phantomjs-prebuilt shrinkpack

# For sshd
RUN mkdir /var/run/sshd
RUN echo 'root:root' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
