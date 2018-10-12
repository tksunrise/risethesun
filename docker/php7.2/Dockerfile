FROM phpdockerio/php72-fpm:latest

# Install selected extensions and other stuff
RUN apt-get update \
    && apt-get -y --no-install-recommends install ssh git-core php7.2-memcached php7.2-mongodb php7.2-mysql php7.2-pgsql php7.2-redis php7.2-imap php7.2-soap php7.2-sqlite3 php7.2-bz2 php7.2-mbstring php7.2-gd php7.2-imagick php7.2-xdebug php7.2-xml php7.2-bcmath pngquant \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer

RUN curl -sL https://deb.nodesource.com/setup_6.x | bash -
RUN apt-get install -y nodejs

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install yarn

RUN mkdir /root/.ssh
COPY id_rsa /root/.ssh
RUN chmod 600 /root/.ssh/id_rsa

WORKDIR "/tksunrise/"