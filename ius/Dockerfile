FROM centos:7

LABEL maintainer="junion-org"

RUN set -x \
    && yum -y update \
    && yum -y install \
        https://repo.ius.io/ius-release-el7.rpm \
        https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
    && yum -y install \
        python35u-devel \
        python35u-pip \
    && rm -rf /var/cache/yum/* \
    && yum clean all \
    && ln -s /usr/bin/python3.5 /usr/local/bin/python \
    && ln -s /usr/bin/pip3.5 /usr/local/bin/pip \
    && ln -nfs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && localedef -f UTF-8 -i ja_JP ja_JP.UTF-8

ENV LANG="ja_JP.UTF-8" \
    LANGUAGE="ja_JP:ja" \
    LC_ALL="ja_JP.UTF-8"
