FROM php:7.0-apache
MAINTAINER ingo.steinke@sevenval.com

# Install git (needed to download grav):
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -yq install \
        git \
    rm -rf /var/lib/apt/lists/*

# Install grav CMS, update updater, and install admin + gitsync plugins:
RUN cd /var/www/html && \
    git clone https://github.com/getgrav/grav.git && \
    cd /var/www/html/grav && \
    bin/grav install && \
    bin/gpm selfupgrade -f && \
    bin/gpm update && \
    bin/gpm install admin && \
    bin/gpm install git-sync

# Do we need explicit entrypoint/exposure of apache, php, grav application?