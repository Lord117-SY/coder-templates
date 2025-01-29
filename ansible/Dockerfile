FROM ubuntu:24.04
COPY files/python_argcomplete /etc/skel/.bash_completion
RUN apt-get update \
    && apt-get install -y \
    sudo \
    curl \
    wget \
    ansible \
    ansible-core \
    ansible-lint \
    python3-argcomplete \
    python3-pip \
    git-core \
    bash-completion \
    sshpass \
    && rm -rf /var/lib/apt/lists/*

ARG USER=coder
RUN useradd --groups sudo --no-create-home --shell /bin/bash ${USER} \
    && echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
    && chmod 0440 /etc/sudoers.d/${USER} \
    && echo "export LANG=POSIX" >> /etc/skel/.bashrc
USER ${USER}
WORKDIR /home/${USER}
