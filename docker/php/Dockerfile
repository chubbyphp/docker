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
    php82-php-ast \
    php82-php-bcmath \
    php82-php-cli \
    php82-php-devel \
    php82-php-fpm \
    php82-php-gd \
    php82-php-intl \
    php82-php-mbstring \
    php82-php-opcache \
    php82-php-pecl-amqp \
    php82-php-pecl-apcu \
    php82-php-pecl-memcached \
    php82-php-pecl-mongodb \
    php82-php-pecl-pcov \
    php82-php-pecl-rdkafka6 \
    php82-php-pecl-redis \
    php82-php-pecl-swoole6 \
    php82-php-pecl-xdebug3 \
    php82-php-pecl-zip \
    php82-php-pgsql \
    php82-php-sodium \
    php82-php-xml \
    procps-ng \
    sudo \
    supervisor \
    unzip \
    vim \
    zsh

RUN ln -sf /usr/bin/php82 /usr/bin/php \
    && rm /etc/opt/remi/php82/php.d/15-xdebug.ini \
    && rm /etc/opt/remi/php82/php.d/40-pcov.ini

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
    && npm install -g @anthropic-ai/claude-code --allow-scripts=@anthropic-ai/claude-code \
    && mkdir -p "$HOME/.claude"

RUN source ~/.bashrc \
    && npm install -g @openai/codex \
    && mkdir -p "$HOME/.codex"

RUN source ~/.bashrc \
    && npm install -g opencode-ai@latest --allow-scripts=opencode-ai \
    && mkdir -p "$HOME/.config/opencode" \
    && mkdir -p "$HOME/.local/share/opencode"

RUN source ~/.bashrc \
    && npm install -g @earendil-works/pi-coding-agent --allow-scripts=@google/genai,protobufjs \
    && mkdir -p "$HOME/.pi/agent" \
    && pi install git:github.com/huggingface/pi-llama

WORKDIR /app

CMD /usr/bin/supervisord
