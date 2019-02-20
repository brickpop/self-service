FROM node:8-alpine

WORKDIR /cryptpad

RUN apk --no-cache add --virtual ephemeral-deps git tini \
    && git clone https://github.com/xwiki-labs/cryptpad.git --branch 2.17.0 . \
    && npm install --production \
    && npm install -g bower \
    && bower install --allow-root \
    && npm uninstall -g bower \
    && rm -Rf /root/.npm \
    && apk del ephemeral-deps

ADD ./config.example.js .

EXPOSE 3000

# VOLUME /cryptpad/datastore
# VOLUME /cryptpad/customize

ENV USE_SSL=false
ENV STORAGE='./storage/file'
ENV LOG_TO_STDOUT=true

CMD ["/sbin/tini", "--", "/cryptpad/container-start.sh"]
