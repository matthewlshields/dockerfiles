FROM ubuntu:trusty
LABEL maintainer="Matthew L. Shields"
LABEL maintainer.email="geek@shields.cc"


RUN apt-get update \
    && apt-get install -y \
        apt-transport-https \
        gnupg \
        curl \
        ca-certificates \
        --no-install-recommends \
	    && rm -rf /var/lib/apt/lists/*

RUN AZ_REPO=$(lsb_release -cs) \
    && echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | \
    sudo tee /etc/apt/sources.list.d/azure-cli.list

RUN apt-key adv --keyserver packages.microsoft.com --recv-keys 52E16F86FEE04B979B07E28DB02C46DF417A0893 \
    && curl -L https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add - \
    && apt-get update \
    && sudo apt-get install -y \
        azure-cli

ENTRYPOINT [ "az" ]