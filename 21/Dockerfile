FROM openjdk:21-slim-bookworm
MAINTAINER sys@qmimi.net
ENV TZ=Asia/Shanghai
ENV LANG C.UTF-8
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ARG user=qmm
ARG group=qmm
ARG uid=1000
ARG gid=1000
ARG ARG_HOME=/usr/share/work
ENV HOME ${ARG_HOME}
ENV USER qmm


RUN apt-get update && apt-get install net-tools -y
RUN apt-get update && apt-get install vim -y
RUN apt-get update && apt-get install telnet -y
RUN apk update && apk upgrade && apk add ca-certificates && update-ca-certificates && rm -rf /var/cache/apk/*


ENV PATH /usr/share/work:/usr/local/bin:/usr/local/bin/gosu:$PATH


RUN groupadd -g ${gid} ${group} \
    && useradd -d "$HOME" -u ${uid} -g ${gid} -m -s /bin/bash ${user}

WORKDIR ${ARG_HOME}
