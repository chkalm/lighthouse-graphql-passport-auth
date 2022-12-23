FROM debian:buster

# Update packages and server
RUN apt update && apt upgrade -y

# Install base packages
RUN apt install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2 wget curl
# RUN apt install -y net-tools vim nano htop git sudo

# Add repositories
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/sury-php.list
RUN wget -qO - https://packages.sury.org/php/apt.gpg | apt-key add -
RUN apt update

# RUN apt install -y libzip-dev libpq-dev libxml2-dev zlib1g-dev

# Install PHP 8.1 and extensions
RUN apt install -y php8.1 php8.1-curl php8.1-mbstring php8.1-zip php8.1-xml php8.1-sqlite3 php8.1-cli

# Install composer
RUN wget https://raw.githubusercontent.com/composer/getcomposer.org/76a7060ccb93902cd7576b67264ad91c8a2700e2/web/installer -O - -q \
        | php -- --filename=composer --install-dir=/usr/bin --version=2.2.6

# Final update
RUN apt update && apt upgrade -y