FROM debian:bookworm-slim

LABEL maintainer="knid"

ENV PRIVATE_KEY=
ENV PORT=51820
ENV CIDR=10.8.0.1/24
ENV WG_CONFIG_PATH=/etc/wireguard/wg0.conf
ENV WG_PRIVATE_KEY_PATH=/etc/wireguard/private.key
ENV WG_PUBLIC_KEY_PATH=/etc/wireguard/public.key
ENV DEFAULT_PEERS=

COPY . /

RUN apt update && apt install wireguard iptables iproute2 -y

EXPOSE 51820/udp

ENTRYPOINT [ "sh", "start" ]
