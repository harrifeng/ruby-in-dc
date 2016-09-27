# image name: harrifeng/opts
FROM ubuntu:14.04
RUN apt-get update && \
DEBIAN_FRONTEND=noninteractive apt-get -y install \
gcc \
make \
libssl-dev \
libreadline-dev \
zlib1g-dev \
libmysqlclient-dev \
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
mysql-client \
sudo \
wget \
openssh-server

# For sshd
RUN mkdir /var/run/sshd
RUN echo 'root:root' | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
