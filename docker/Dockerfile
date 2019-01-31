FROM nginx:1.15.1

RUN \
  apt-get update \
  && apt-get -y install gettext-base \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN rm /etc/nginx/conf.d/default.conf && \
mkdir -m 755 /app

COPY ./docker/config/nginx.conf /etc/nginx/nginx/conf
COPY ./docker/config/server.conf.template /etc/nginx/conf.d/server.conf.template
COPY . /app

RUN ln -sf /dev/stdout /var/log/nginx/access.log && \
ln -sf /dev/stdout /var/log/nginx/error.log