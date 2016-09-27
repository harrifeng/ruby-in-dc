# image name: harrifeng/opts
FROM harrifeng/basic:14.04
RUN apt-get update && \
DEBIAN_FRONTEND=noninteractive apt-get -y install \
gcc \
make \
libssl-dev \
libreadline-dev \
zlib1g-dev \
libmysqlclient-dev \
libsqlite3-dev

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
