FROM ubuntu:xenial

RUN \
  apt-get update && apt-get upgrade -q -y && \
  apt-get install -y --no-install-recommends golang git make gcc libc-dev ca-certificates && \
  git clone --depth 1 https://github.com/EthereumVega/weth && \
  (cd go-ethereum && make weth) && \
  cp go-ethereum/build/bin/weth /weth && \
  apt-get remove -y golang git make gcc libc-dev && apt autoremove -y && apt-get clean && \
  rm -rf /go-ethereum

EXPOSE 8285
EXPOSE 30313

ENTRYPOINT ["/weth"]
