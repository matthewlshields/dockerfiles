# Visual Studio Code in a container
#	NOTE: Needs the redering device (yeah... idk)
#
# Shamelessly based off of the work by Jess Frazelle (https://github.com/jessfraz)
#
# docker run -d -v /tmp/.X11-unix:/tmp/.X11-unix -v $HOME:/home/user -e DISPLAY=unix$DISPLAY --device /dev/dri --name vscode1 mls/vscode

FROM fedora:27
LABEL maintainer "Matthew L. Shields <geek@shields.cc>"

RUN dnf update -y && dnf install -y gnupg git

# Add the vscode repo
RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
RUN sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
RUN dnf check-update

RUN dnf update -y && dnf -y install \
	code \
	libX11-xcb \
	libXcomposite \
	libXcursor \
	libXdamage \
	libXext \
	libXfixes \
	libXi \
	libXrandr \
	libXrender \
	libXtst \
	which

ENV HOME /home/user
RUN useradd --create-home --home-dir $HOME user \
	&& chown -R user:user $HOME

COPY start.sh /usr/local/bin/start.sh
RUN chmod +x /usr/local/bin/start.sh

WORKDIR $HOME

CMD [ "start.sh" ]

