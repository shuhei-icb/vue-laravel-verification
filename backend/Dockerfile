FROM php:8.4-fpm

# 必要なパッケージをインストール
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    unzip \
    libonig-dev \
    libxml2-dev \
    npm \
    nodejs \
    && docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Composerインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# 作業ディレクトリ設定
WORKDIR /var/www

# 権限を整える（好みに応じて）
RUN chown -R www-data:www-data /var/www

# ポート解放（FPMは9000）
EXPOSE 9000

# 起動コマンド（FPM起動）
CMD ["php-fpm"]
