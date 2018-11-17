#
# build with (note build context if required):
# docker build -t ubuntu_c_dev-env:latest -f path/to/Dockerfile .
#
# run with:
# docker run -it -v /path/to/volume/for/mounting:/root/mount_location --cap-add=SYS_PTRACE --security-opt seccomp=unconfined --rm ubuntu_c_dev-env
#

FROM ubuntu:rolling

LABEL version="v1.0.0" description="slim Ubuntu-based C dev environment image"
MAINTAINER steve

RUN apt-get update && apt-get install -y \
    build-essential \
    gfortran \
    gcc \
    g++ \
    gdb \
    libreadline-dev \
    valgrind \
    vim	\
    screen \
    git \
    nano \
    man 

RUN git config --global user.name "chewdonkey"
RUN git config --global user.email "chewdonkey@gmail.com"

#Avoid using env variables, use -I -L -l and -Wl,-rpath,/path/to/dir instead

COPY /configs/vim/.vimrc /root
COPY /configs/screen/.screenrc /root
WORKDIR /root

ENTRYPOINT ["/bin/bash"]