FROM ubuntu:trusty

MAINTAINER Gordon Freeman <eax@gmx.us>

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt-key update && \
    apt-get update && \
    apt-get upgrade -y && \
    echo "Etc/UTC" > /etc/timezone && \
    dpkg-reconfigure -f noninteractive tzdata && \
    apt-get install -y --no-install-recommends --no-install-suggests \
        ca-certificates \
        curl && \
    mkdir -p /usr/local/bin && \
    curl https://raw.githubusercontent.com/tj/n/master/bin/n -o /usr/local/bin/n  && \
    chmod +x /usr/local/bin/n  && \
    n stable || true && \
    apt-get remove --purge -y curl $(apt-mark showauto) && \
    apt-get autoremove --purge -y && \
    rm -rf /var/lib/apt/lists/*

CMD ["bash"]
