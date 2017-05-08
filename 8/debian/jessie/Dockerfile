FROM debian:jessie

RUN set -ex; \
    echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" | \
         tee    /etc/apt/sources.list.d/webupd8team-java.list; \
    echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" | \
         tee -a /etc/apt/sources.list.d/webupd8team-java.list; \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886; \
    echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections; \
    echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections; \
    apt-get update; \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
            oracle-java8-installer \
            oracle-java8-set-default \
            ; \
    rm -rf /var/cache/oracle-jdk8-installer; \
    rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME /usr/lib/jvm/java-8-oracle
