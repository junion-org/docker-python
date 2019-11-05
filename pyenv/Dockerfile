FROM centos:7

LABEL maintainer="junion-org"

ARG python_version

ENV HOME="/root"
ENV PYENV_ROOT="$HOME/.pyenv"
ENV PATH="$PYENV_ROOT/bin:$PATH"

RUN set -x \
    && yum -y update \
    && yum -y install \
        gcc \
        git \
        make \
        zlib-devel \
        bzip2-devel \
        readline-devel \
        sqlite-devel \
        openssl-devel \
        tk-devel \
        libffi-devel \
        ncurses-devel \
        libxml2-devel \
        gdbm-devel \
        libuuid-devel \
    && rm -rf /var/cache/yum/* \
    && yum clean all \
    && ln -nfs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && localedef -f UTF-8 -i ja_JP ja_JP.UTF-8 \
    && git clone https://github.com/pyenv/pyenv.git $PYENV_ROOT \
    && echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc \
    && eval "$(pyenv init -)" \
    && CFLAGS="-fPIC" pyenv install $python_version \
    && pyenv global $python_version \
    && pip install --upgrade pip

ENV LANG="ja_JP.UTF-8" \
    LANGUAGE="ja_JP:ja" \
    LC_ALL="ja_JP.UTF-8"
