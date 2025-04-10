FROM ubuntu:16.04

LABEL version="1.0"
LABEL description="Install any package using SDKMan"

ENV SDKMAN_DIR /root/.sdkman
ENV GRAILS_VERSION 3.3.9
ENV JAVA_VERSION 17.0.8-tem

RUN mkdir -p /apps/home
RUN apt-get update && apt-get install -y zip curl unzip

RUN rm /bin/sh && ln -s /bin/bash /bin/sh
RUN curl -s "https://get.sdkman.io" | bash

RUN bash -c "source $SDKMAN_DIR/bin/sdkman-init.sh && \
    echo 'sdkman_auto_answer=true' > $SDKMAN_DIR/etc/config && \
    echo 'sdkman_auto_selfupdate=false' >> $SDKMAN_DIR/etc/config && \
    echo 'sdkman_insecure_ssl=false' >> $SDKMAN_DIR/etc/config"

RUN bash -c "source $SDKMAN_DIR/bin/sdkman-init.sh && sdk install java $JAVA_VERSION"
RUN bash -c "source $SDKMAN_DIR/bin/sdkman-init.sh && sdk install grails $GRAILS_VERSION"

WORKDIR /apps/home

EXPOSE 8080
ENTRYPOINT ["./docker-entry.sh"]
