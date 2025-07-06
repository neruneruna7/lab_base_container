FROM ubuntu:24.04
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    openssh-server python3 python3-pip curl ca-certificates git build-essential sudo \
  && mkdir /var/run/sshd \
  && echo 'root:password' | chpasswd \
  && sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN curl -Ls https://astral.sh/uv/install.sh | bash

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
