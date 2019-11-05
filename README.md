# docker-python

Dockerfile for Python

The locale and time zone are set for the Japanese environment.

## Versions

Checked on November 5th, 2019.

### CentOS 7

If you want to use...

- Python 3.7, use pyenv.
- Python 3.6, use base.
- Python 3.5, use ius.
- Python 3.4, use ius (epel).
- Other versons, use pyenv.

OK, but why?

- base
    - Only Python 3.6.8 is available.
    ```
    $ yum list --showduplicates | grep python3-devel
    python3-devel.i686                           3.6.8-10.el7               base
    python3-devel.x86_64                         3.6.8-10.el7               base
    ```
- ius
    - Python 3.4.8 (epel), 3.5.6 (ius), and 3.6.8 (base) are available.
        - Package python34u is obsoleted by python34, trying to install python34-3.4.10-4.el7.x86_64 (epel) instead
        - Package python36u is obsoleted by python3, trying to install python3-3.6.8-10.el7.x86_64 (base) instead
    ```
    $ yum install -y https://centos7.iuscommunity.org/ius-release.rpm
    $ yum list --showduplicates | grep python34u-devel
    python34u-devel.x86_64                    3.4.8-1.ius.el7                ius
    $ yum list --showduplicates | grep python35u-devel
    python35u-devel.x86_64                    3.5.6-1.ius.el7                ius
    $ yum list --showduplicates | grep python36u-devel
    python36u-devel.x86_64                    3.6.8-1.el7.ius                ius
    ```
- pyenv
    - Any version is available.

| version | base/ius | pyenv |
| --- | --- | --- |
| 3.7.4 | - |  |
| 3.6.8 | 457MB |  |
| 3.5.6 |  |  |
| 3.4.8 |  |  |

### Alpine Linux

- Use official images.
    - https://hub.docker.com/_/python

## Installation

### base/ius

```bash
# clone repo
$ git clone https://github.com/junion-org/docker-python.git

# use base
$ cd base/

# or use ius
$ cd ius/

# build image
# ex) $ docker build -t python:3.5.6-centos7 .
$ docker build -t IMAGE:TAG .
```

### pyenv

```bash
# clone repo
$ git clone https://github.com/junion-org/docker-python.git

# use pyenv
$ cd pyenv/

# build image
# ex) $ docker build --build-arg python_version=3.7.4 -t python:3.6.8-centos7 .
$ docker build --build-arg python_version=VERSION -t IMAGE:TAG .
```
