FROM ubuntu:jammy

RUN apt-get update && apt-get install -y \
    ffmpeg \
    libsm6 \
    libxext6 \
    python3 \
    python3-pip \
    git \
    curl \
    wget \
    unzip \
    vim \
    graphviz \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt /tmp/
RUN pip install --no-cache-dir -r /tmp/requirements.txt

ARG USER_UID=1000
ARG USER_GID=1000
ARG USER_NAME

RUN groupadd --gid ${USER_GID} ${USER_NAME} && \
    useradd --create-home --gid ${USER_GID} --uid ${USER_UID} ${USER_NAME} && \
    usermod -aG sudo ${USER_NAME} && \
    echo "${USER_NAME} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && \
    mkdir -p /home/${USER_NAME} && \
    chown -R ${USER_UID}:${USER_GID} /home/${USER_NAME} && \
    mkdir /home/${USER_NAME}/workspace
USER ${USER_NAME}
WORKDIR /home/${USER_NAME}/workspace

SHELL [ "/bin/bash", "-c" ]
ENV SHELL=/bin/bash