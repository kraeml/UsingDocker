FROM debian

MAINTAINER Micheal Schaar <kraeml@sesamestreet.franken.de>
RUN apt-get update && apt-get install -y cowsay fortune
COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
