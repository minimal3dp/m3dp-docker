FROM ubuntu/nginx:1.18-22.04_beta

ARG DEBIAN_FRONTEND=noninteractive
ARG KIAUH_BRANCH="master"
#ARG USER=m3dp
#ARG HOME=/home/${USER}

#RUN useradd -d ${HOME} -ms /bin/bash ${USER}

RUN apt-get update && apt-get install -y \
    sudo \
    git \
    locales && rm -rf /var/lib/apt/lists/* \
	&& localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8

ENV LANG en_US.utf8

#RUN useradd --user-group --no-log-init --shell /bin/false -m -d ${HOME} ${USER} && \
    #groupadd -g ${DEVICE_GID} ${DEVICE_GROUP} && \
    #usermod -a -G ${DEVICE_GROUP} ${USER} && \
    #usermod -a -G tty ${USER} && \
    #usermod -a -G dialout ${USER}

#USER ${USER}
#WORKDIR ${HOME}

### Klipper setup ###
RUN git clone --single-branch --branch ${KIAUH_BRANCH} https://github.com/th33xitus/kiauh.git kiauh

#VOLUME ${HOME}

ARG USER=m3dp
ARG HOME=/home/${USER}
RUN useradd -d ${HOME} -ms /bin/bash ${USER}

EXPOSE 80

