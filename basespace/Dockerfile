FROM python:3.9.15

RUN apt-get update && apt-get install -y wget tar curl

RUN wget "https://launch.basespace.illumina.com/CLI/latest/amd64-linux/bs" -O /opt/bs && \
    chmod a+x /opt/bs

ENV PATH /opt:$PATH

# copy config file (authenticated) from ~/.basespace
COPY ./bs/default.cfg /root/.basespace/