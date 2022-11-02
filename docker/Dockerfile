FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive
ARG KIAUH_BRANCH="master"
ARG USER=m3dp
ARG HOME=/home/${USER}

RUN useradd -d ${HOME} -ms /bin/bash ${USER}

RUN apt-get update && apt-get install -y \
    ubuntu-server \
    bash \
    curl \
    git \
    # Clean up
    apt-get autoremove -y && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

#RUN useradd --user-group --no-log-init --shell /bin/false -m -d ${HOME} ${USER} && \
    #groupadd -g ${DEVICE_GID} ${DEVICE_GROUP} && \
    #usermod -a -G ${DEVICE_GROUP} ${USER} && \
    #usermod -a -G tty ${USER} && \
    #usermod -a -G dialout ${USER}

USER ${USER}
WORKDIR ${HOME}

### Klipper setup ###
RUN git clone --single-branch --branch ${KIAUH_BRANCH} https://github.com/th33xitus/kiauh.git kiauh

VOLUME ${HOME}

#EXPOSE 7125

