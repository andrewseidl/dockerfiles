# Remove DRI and privileged args to run purely CPU.
#
# docker run \
#   -v /tmp/.X11-unix:/tmp/.X11-unix \
#   -v /dev/dri:/dev/dri:rw \
#   --privileged=true \
#   -e DISPLAY=$DISPLAY \
#   -v /home:/data \
#   fsv2


FROM debian:jessie
MAINTAINER Andrew Seidl <dev@aas.io>

RUN apt-get update && apt-get install -y \
    curl \
    build-essential \
    libftgl-dev \
    libgl1-mesa-dri \
    libgtkgl2.0-dev \
    libgtkmm-2.4-dev \
    --no-install-recommends

RUN cd /usr/src && \
    curl -O http://fedorchenko.net/src/fsv2-1.1.0.tar.bz2 && \
    tar jxvf fsv2-1.1.0.tar.bz2 && \
    cd fsv2-1.1.0 && \
    ./configure && \
    make

RUN apt-get install -y \

WORKDIR /data
 
ENTRYPOINT [ "/usr/src/fsv2-1.1.0/src/fsv2" ]
