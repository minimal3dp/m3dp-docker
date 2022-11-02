
FROM debian:bullseye-slim as image

ARG DEBIAN_FRONTEND=noninteractive
ARG KIAUH_BRANCH="master"
ARG USER=m3dp
ARG HOME=/home/${USER}

RUN useradd -d ${HOME} -ms /bin/bash ${USER}
RUN apt-get update && \
    apt-get install -y \
    bash \
    curl \
    git \
    gpiod \
    iproute2 \
    libcurl4-openssl-dev \
    libjpeg-dev \
    liblmdb-dev \
    libopenjp2-7 \
    libsodium-dev \
    libssl-dev \
    libtiff5 \
    locales \
    rsync \
    supervisor \
    zlib1g-dev && \
    sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen && \
    # Clean up
    apt-get autoremove -y && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

ENV LC_ALL en_US.UTF-8 
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en   

ARG DEVICE_GROUP=device
ARG DEVICE_GID=987


RUN useradd --user-group --no-log-init --shell /bin/false -m -d ${HOME} ${USER} && \
    groupadd -g ${DEVICE_GID} ${DEVICE_GROUP} && \
    usermod -a -G ${DEVICE_GROUP} ${USER} && \
    usermod -a -G tty ${USER} && \
    usermod -a -G dialout ${USER}

USER ${USER}
WORKDIR ${HOME}

### Klipper setup ###
RUN git clone --single-branch --branch ${KIAUH_BRANCH} https://github.com/th33xitus/kiauh.git kiauh

VOLUME ${HOME}

#EXPOSE 7125


