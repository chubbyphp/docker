FROM rockylinux/rockylinux:10.0

SHELL ["/bin/bash", "-c"]

RUN dnf upgrade -y --refresh

RUN dnf install -y epel-release https://rpms.remirepo.net/enterprise/remi-release-10.rpm

RUN dnf install -y --nobest \
    git \
    glibc-langpack-de \
    langpacks-de \
    libatomic \
    nmap-ncat \
    php84-php-ast \
    php84-php-bcmath \
    php84-php-cli \
    php84-php-devel \
    php84-php-fpm \
    php84-php-gd \
    php84-php-intl \
    php84-php-mbstring \
    php84-php-opcache \
    php84-php-pecl-amqp \
    php84-php-pecl-apcu \
    php84-php-pecl-memcached \
    php84-php-pecl-mongodb \
    php84-php-pecl-pcov \
    php84-php-pecl-rdkafka6 \
    php84-php-pecl-redis \
    php84-php-pecl-swoole6 \
    php84-php-pecl-xdebug3 \
    php84-php-pecl-zip \
    php84-php-pgsql \
    php84-php-sodium \
    php84-php-xml \
    procps-ng \
    sudo \
    supervisor \
    unzip \
    vim \
    zsh

RUN ln -sf /usr/bin/php84 /usr/bin/php \
    && rm /etc/opt/remi/php84/php.d/15-xdebug.ini \
    && rm /etc/opt/remi/php84/php.d/40-pcov.ini

ENV TZ=Europe/Zurich

RUN echo "LANG=de_CH.UTF-8" > /etc/locale.conf \
    && cp -f /usr/share/zoneinfo/${TZ} /etc/localtime

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

COPY docker/php/files /

ARG USER_ID
ARG GROUP_ID

RUN getent group ${GROUP_ID} >/dev/null || groupadd -g ${GROUP_ID} php \
    && useradd -u ${USER_ID} -g ${GROUP_ID} -s /bin/bash -M php \
    && chown -Rf php: /home/php \
    && echo 'php ALL=(ALL) NOPASSWD: ALL' > '/etc/sudoers.d/php'

USER php

WORKDIR /home/php

RUN curl -fsSL https://fnm.vercel.app/install | bash -s -- --install-dir "$HOME/.fnm" --skip-shell \
    && source ~/.bashrc \
    && fnm install 24 \
    && fnm default 24 \
    && fnm use 24 \
    && npm install -g corepack@latest

RUN source ~/.bashrc \
    && npm install -g @anthropic-ai/claude-code \
    && mkdir -p "$HOME/.claude"

RUN source ~/.bashrc \
    && npm install -g @openai/codex \
    && mkdir -p "$HOME/.codex"

RUN source ~/.bashrc \
    && npm install -g opencode-ai@latest \
    && mkdir -p "$HOME/.config/opencode" \
    && mkdir -p "$HOME/.local/share/opencode"

RUN source ~/.bashrc \
    && npm install -g @earendil-works/pi-coding-agent \
    && mkdir -p "$HOME/.pi/agent"

WORKDIR /app

CMD /usr/bin/supervisord
