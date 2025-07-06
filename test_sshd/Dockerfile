# ベースイメージは Debian か Ubuntu をベースにしているものにする
FROM ubuntu:22.04

USER root

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update --yes \
    && apt-get upgrade --yes \
    && apt-get install --yes --no-install-recommends \
        # - `tini` is installed as a helpful container entrypoint,
        #   that reaps zombie processes and such of the actual executable we want to start
        #   See https://github.com/krallin/tini#why-tini for details
        tini \
        openssh-server \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN mkdir /var/run/sshd
RUN echo 'root:screencast' | chpasswd

# 以下の設定書き換えコマンドはバージョンによって微妙に変える必要がある
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

CMD ["tini", "-g", "--"]