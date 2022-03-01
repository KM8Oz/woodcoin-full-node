FROM ubuntu:18.04
MAINTAINER km8oz
WORKDIR /root
RUN apt-get update
RUN apt-get -y install apt-utils pkg-config software-properties-common
RUN add-apt-repository ppa:bitcoin/bitcoin -y
RUN apt-get update
# ARG user=user0
# ARG group=user0
# ARG uid=1000
# ARG gid=1000
# RUN groupadd -g ${gid} ${group} && useradd -u ${uid} -G ${group} -s /bin/sh -D ${user}

# installing an editor is not necessary, but is handy
RUN apt-get -y install wget multiarch-support libdb++-dev libreadline-dev
RUN export TERM=xterm-256color
# RUN echo "alias ll='ls -l'" >> /root/.bashrc
# RUN bash -c "history -a"
# RUN ls
COPY ./context/* ./
RUN tar -xzvf ./woodcoin.tar.gz 
RUN for i in `cat ./listboostlib.txt`; do wget $i; done
RUN dpkg -i *.deb
RUN chmod -R +x ./woodcoin*
RUN cp ./woodcoin* /usr/bin/
# USER ${user}
# RUN woodcoind -daemon -upnp -debugnet
#for i in `cat ./context/listboostlib.txt`; do echo $i; done
# RUN ["tail", "-f /dev/null"]
# docker build --no-cache -t woodcoin-full-node:latest -f dockerfiles/Dockerfile context
# woodcoind -rescan
 # (default: 9332 or testnet: 19332)