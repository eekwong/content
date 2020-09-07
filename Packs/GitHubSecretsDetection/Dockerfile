FROM demisto/python3:3.8.5.10845

LABEL maintainer="Matthew Kwong"

COPY trufflehog.patch /

RUN apk add --no-cache \
        git \
    && apk add --no-cache --virtual .build-deps \
        make \
    && git config --global http.sslVerify "false" \
    && pip install trufflehog==2.1.11 \
    && apk del --no-cache .build-deps \
    && cd /usr/local/lib/python3.8/site-packages/ \
    && git apply /trufflehog.patch
