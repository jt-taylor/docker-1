FROM debian:latest
RUN apt-get update -y && apt-get upgrade -y && \
	apt-get install -y wget && \
	apt-get install -y curl openssh-server ca-certificates postfix

WORKDIR /
RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
RUN chmod 777 ./script.deb.sh && ./script.deb.sh 
#RUN apt-get update -y && EXTERNAL_URL="http://gitlab.example.com" apt-get install -y gitlab-ce
RUN apt-get install -y gitlab-ce
RUN apt-get update && apt-get install -y tzdata && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp* /var/tmp/*

EXPOSE 22 80 433
ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure \
	&& tail -f /dev/null
#docker build -t ex03 .
# so for some reason the gitlab doesn't have a defualt password so when you get
#	onto the web client it just gives you errrors when you try to add/reset the password
#	we can fix this by adding (--env / -e) GITLAB_ROOT_PASSWORD='password here'
#docker run --privileged -e GITLAB_ROOT_PASSWORD=root --restart=unless-stopped -it -p 8022:22 -p 8080:80 -p 8433:433 --name gitlab1 ex03:latest
