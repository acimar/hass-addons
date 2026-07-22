ARG BUILD_FROM=ghcr.io/home-assistant/amd64-base:3.23
FROM ${BUILD_FROM}

SHELL ["/bin/ash", "-o", "pipefail", "-c"]

RUN apk add --no-cache \
    bash \
    jq \
    git \
    py3-pip \
    py3-aiohttp \
    py3-gobject3 \
    gstreamer \
    gst-plugins-base \
    gst-plugins-good \
    gst-plugins-bad \
    gst-plugins-ugly \
    gst-libav \
    libnice-gstreamer

WORKDIR /app
# Install the patched core straight from the fork branch (avoids relying on
# git submodule init during the Home Assistant add-on build).
ARG CORE_REF=feat/configurable-audio-codec-opus
RUN pip3 install --break-system-packages --no-deps \
    "git+https://github.com/acimar/sip-indoor-station.git@${CORE_REF}"

COPY run.sh /run.sh
RUN chmod a+x /run.sh

CMD ["/run.sh"]
