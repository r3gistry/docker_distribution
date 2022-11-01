FROM golang:1.18-alpine3.16

WORKDIR /tmp/

ADD \
https://github.com/distribution/distribution/archive/v2.8.0.tar.gz \
.

RUN \
apk add --no-cache git make \
&& tar -xvf v2.8.0.tar.gz \
&& mkdir -p $GOPATH/src/github.com/distribution/distribution/ \
&& mv distribution-2.8.0/* $GOPATH/src/github.com/distribution/distribution/ \
&& rm -r * \
&& cd $GOPATH/src/github.com/distribution/distribution/ \
&& CGO_ENABLED=0 BUILDTAGS=include_oss:include_gcs make clean binaries \
&& mv bin/registry /usr/local/bin/distribution \
&& chmod +x /usr/local/bin/distribution \
&& cd $GOPATH/src/ \
&& rm -r * \
&& apk del git make


FROM alpine:3.16

LABEL maintainer="R3GISTRY"
LABEL description="Distribution in Docker. This is a opensource registry."

COPY --from=0 /usr/local/bin/distribution /usr/local/bin/

RUN \
apk add --no-cache ca-certificates apache2-utils

VOLUME ["/mnt/distribution/"]

ENTRYPOINT ["distribution"]
CMD ["-h"]
