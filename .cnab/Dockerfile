FROM debian:stretch-slim

ARG BUNDLE_DIR

RUN apt-get update && apt-get install -y ca-certificates

# exec mixin has no buildtime dependencies

RUN apt-get update && apt-get install -y curl
RUN curl https://get.helm.sh/helm-v3.3.4-linux-amd64.tar.gz --output helm3.tar.gz
RUN tar -xvf helm3.tar.gz
RUN mv linux-amd64/helm /usr/local/bin/helm3

COPY . $BUNDLE_DIR
RUN rm $BUNDLE_DIR/porter.yaml
RUN rm -fr $BUNDLE_DIR/.cnab
COPY .cnab /cnab
WORKDIR $BUNDLE_DIR
CMD ["/cnab/app/run"]