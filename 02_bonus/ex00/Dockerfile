FROM debian:latest

RUN apt-get update && apt-get install -qq cowsay fortune lolcat

ENTRYPOINT /usr/games/fortune | /usr/games/cowsay | /usr/games/lolcat

# i mean this one is pretty simple

#this is from the https://forum.intra.42.fr/topics/19247/messages?page=1#93483
# docker build -t bonus_00
# docker run --rm -t bonus00
