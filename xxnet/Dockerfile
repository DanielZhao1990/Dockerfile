FROM ubuntu:16.04
MAINTAINER daniel

ENV _XXNET_VERSION 3.13.1
WORKDIR /root/XX-Net-"$_XXNET_VERSION"
#ADD  "$_XXNET_VERSION" /root
#ADD  https://codeload.github.com/XX-net/XX-Net/zip/"$_XXNET_VERSION" /root
ADD  https://github.com/XX-net/XX-Net/archive/"$_XXNET_VERSION".tar.gz /root
COPY "$_XXNET_VERSION" /root
# 把/root/3.13.1解压为/root/XX-Net-3.13.1
RUN tar -zxf /root/"$_XXNET_VERSION" -C /root
#RUN apk add --no-cache py-openssl
RUN sed -i "s/allow_remote_connect\"], 0/allow_remote_connect\"], 1/" code/default/launcher/config.py
RUN rm /root/"$_XXNET_VERSION"
#RUN  sed -i "s/allow_remote_connect: 0/allow_remote_connect: 1/" \
#	data/launcher/config.yaml
VOLUME /root/XX-Net-"$_XXNET_VERSION"/data/gae_proxy/
# COPY manual.ini data/gae_proxy/manual.ini
COPY client.json data/x_tunnel/client.json
COPY config.json data/gae_proxy/config.json
EXPOSE 8087 8085 1080
CMD ["/bin/bash","-c", "./start"]
