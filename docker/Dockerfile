# Dockerfile: Defines container specifications to startup and run.
# Author: Arthur Cadore M. Barcella
# Github: arthurcadore
# Capacitação Redes - PV Intelbras

# Use Alpine Linux as base image
FROM alpine:latest

# Install OpenSSH server
RUN apk update && \
    apk add openssh && \
    rm -rf /var/cache/apk/*

# Generate host keys
RUN ssh-keygen -A

# Add user "capacita" with password "capacitapass"
RUN adduser -D capacita
RUN echo "capacita:capacitapass" | chpasswd

COPY docker/startup.sh /usr/sbin/startup.sh

RUN chmod +x /usr/sbin/startup.sh

# Start SSH server and keep container running
CMD ["/usr/sbin/startup.sh"]