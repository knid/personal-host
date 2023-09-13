FROM golang:1.21.1-alpine3.18 as build

LABEL maintainer="knid"

ARG ARCH=x86-64
ARG VERSION=2.1.5

WORKDIR /dnscrypt-proxy

RUN apk update && apk add git
RUN git clone https://github.com/DNSCrypt/dnscrypt-proxy src

WORKDIR /dnscrypt-proxy/src/dnscrypt-proxy

RUN go build -o /dnscrypt-proxy/dnscrypt-proxy

FROM alpine:latest

COPY dnscrypt-proxy.toml /dnscrypt-proxy.toml
COPY --from=build /dnscrypt-proxy/dnscrypt-proxy /dnscrypt-proxy

CMD [ "./dnscrypt-proxy" ]