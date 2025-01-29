FROM ubuntu:24.04
RUN apt-get update \
    && apt-get install -y \
    sudo \
    curl \
    wget \
    git-core \
    ksh \
    shellcheck \
    shfmt \
    locales-all \
    && rm -rf /var/lib/apt/lists/*

ARG USER=coder
RUN useradd --groups sudo --no-create-home --shell /usr/bin/ksh ${USER} \
    && echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
    && chmod 0440 /etc/sudoers.d/${USER} \
    && echo "export LANG=POSIX" >> /etc/skel/.bashrc
USER ${USER}
WORKDIR /home/${USER}
