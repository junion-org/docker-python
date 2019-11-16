FROM centos:7

LABEL maintainer="junion-org"

RUN set -x \
    && yum -y update \
    && yum -y install \
        python3-devel \
    && ln -s /usr/bin/python3 /usr/local/bin/python \
    && ln -s /usr/bin/pip3 /usr/local/bin/pip \
    && ln -nfs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && localedef -f UTF-8 -i ja_JP ja_JP.UTF-8 \
    && yum clean all \
    && rm -rf /var/cache/yum/*

ENV LANG="ja_JP.UTF-8" \
    LANGUAGE="ja_JP:ja" \
    LC_ALL="ja_JP.UTF-8"
