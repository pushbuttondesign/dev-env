#
# build with (note build context if required):
# docker build -t ubuntu_py3_dev-env:latest -f path/to/Dockerfile .
#
# run with:
# docker run -it -v /path/to/volume/for/mounting:/root/mount_location --cap-add=SYS_PTRACE --security-opt seccomp=unconfined --rm ubuntu_py3_dev-env
#

FROM ubuntu:rolling

LABEL version="v1.0.0" description="slim Ubuntu-based Python3 dev environment image"
MAINTAINER steve

RUN apt-get update && apt-get install -y \
    python3-pip \
    python3-dev \
    vim	\
    screen \
    git \
    nano \
    man 
    
RUN pip3 install --upgrade pip
RUN pip3 install --no-cache-dir numpy pandas scipy matplotlib luxpy

ENV PYTHONPATH="/root/code/python/librarys:${PYTHONPATH}" \

#swap to install from git later to avoid dockerfile context dependancy
COPY /configs/vim/.vimrc /root
COPY /configs/screen/.screenrc /root
WORKDIR /root

ENTRYPOINT ["/bin/bash"]