FROM fluent/fluentd:v1.14-1

USER root

RUN apk update && \
    apk add --no-cache --virtual .build-deps \
    build-base ruby-dev && \
    gem install faraday -v 2.8.1 && \
    gem install faraday-net_http -v 3.0.2 && \
    gem install fluent-plugin-elasticsearch && \
    gem sources --clear-all && \
    apk del .build-deps && \
    rm -rf /var/cache/apk/* /home/fluent/.gem/ruby/2.3.0/cache/*.gem

USER fluent

# Copy the Fluentd configuration file
COPY fluent.conf /fluentd/etc/fluent.conf