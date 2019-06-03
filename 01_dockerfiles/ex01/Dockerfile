FROM debian
ENV TS3SERVER_LICENSE=accept
EXPOSE 9987/udp 10011 30033

WORKDIR /home/teamspeak
RUN apt-get update -y &&apt-get upgrade -y && \
	apt-get install bzip2 wget -y &&\
	wget http://dl.4players.de/ts/releases/3.0.13.8/teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2 && \
	bunzip2 *.bz2 && \
	tar -xvf *.tar
WORKDIR teamspeak3-server_linux_amd64
ENTRYPOINT sh ts3server_minimal_runscript.sh
# 9987 voice
# 10011 server query
# 30033 file transport
# You need a seperate docker container for the teamspeak client but the question only wants us to run the serverh
# docker build -t ex01 .
# docker run --rm -it -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ex01
