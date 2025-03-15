FROM alpine:latest

ARG USERNAME=manager
ARG USER_UID=1666
ARG USER_GID=1666

RUN apk add --no-cache \
    bash \
    curl \
    git \
    grep \
    helm \
    k9s \
    kubectl \
    shadow \
    sudo

COPY ez_install /usr/local/bin/ez_install
RUN /usr/local/bin/ez_install \
    -g siderolabs/talos \
    -a talosctl-linux-amd64 \
    -o /usr/local/bin/talosctl

RUN	groupadd --gid $USER_GID $USERNAME \
	&&	useradd -s /bin/bash --uid $USER_UID --gid $USERNAME -m $USERNAME \
	&&	echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME

USER manager