FROM nvidia/cuda:12.9.1-base-ubuntu20.04
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    openssh-server python3 python3-pip curl ca-certificates git build-essential sudo \
  && mkdir /var/run/sshd \
  && echo 'root:password' | chpasswd \
  && sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
