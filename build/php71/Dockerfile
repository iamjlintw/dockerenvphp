FROM php:7.1-fpm
ARG DEV_GID
ARG DEV_UID
ENV TZ=Asia/Taipei
RUN echo "Build number: $DEV_GID $DEV_UID"
RUN groupadd -g $DEV_GID  app
#RUN useradd  -g  app -u $DEV_UID app 
RUN useradd -r -m -p '*' -d /home/app -s /bin/bash -u $DEV_UID -g app app
#RUN usermod -d /home/app app
#RUN usermod -s /bin/bash app
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    curl \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libpng12-dev \
    libfreetype6-dev \
    libssl-dev \
    libmcrypt-dev \
    imagemagick \
  && rm -rf /var/lib/apt/lists/*
 RUN docker-php-ext-install mcrypt \
  # Install the PHP pdo_mysql extention
  && docker-php-ext-install pdo_mysql \
  # Install the PHP pdo_pgsql extention
  && docker-php-ext-install pdo_pgsql \
  # Install the PHP gd library
  && docker-php-ext-configure gd \
    --enable-gd-native-ttf \
    --with-jpeg-dir=/usr/lib \
    --with-freetype-dir=/usr/include/freetype2 && \
    docker-php-ext-install gd

    # Install composer
    # source: https://getcomposer.org/download/
    ##

    RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer
    RUN chmod +rx /usr/bin/composer

    # Install Node.js
    RUN curl -sL https://deb.nodesource.com/setup | bash - && \
    apt-get install -y nodejs
    
