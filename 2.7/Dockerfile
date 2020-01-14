FROM golang:1.13-alpine

WORKDIR /tmp/

ADD \
https://github.com/docker/distribution/archive/v2.7.1.tar.gz \
.

RUN \
apk add --no-cache git make \
&& tar -xvf v2.7.1.tar.gz \
&& mkdir -p $GOPATH/src/github.com/docker/distribution/ \
&& mv distribution-2.7.1/* $GOPATH/src/github.com/docker/distribution/ \
&& rm -r * \
&& cd $GOPATH/src/github.com/docker/distribution/ \
&& CGO_ENABLED=0 BUILDTAGS=include_oss:include_gcs make clean binaries \
&& mv bin/registry /usr/local/bin/ \
&& chmod +x /usr/local/bin/registry \
&& cd $GOPATH/src/ \
&& rm -r * \
&& apk del git make


FROM alpine:3.11

LABEL maintainer="R3GISTRY"
LABEL description="Registry in Docker. This is a Docker registry."

COPY --from=0 /usr/local/bin/registry /usr/local/bin/

RUN \
apk add --no-cache ca-certificates apache2-utils

VOLUME ["/mnt/registry/"]

ENTRYPOINT ["registry"]
CMD ["-h"]
