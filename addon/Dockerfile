ARG BUILD_FROM
FROM $BUILD_FROM

# Refresh the Bookworm base image's public CA store at build time.
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends --only-upgrade ca-certificates \
    && update-ca-certificates --fresh \
    && rm -rf /var/lib/apt/lists/*

COPY run.sh /run.sh
# The integration workflow stages its own locked build and source assets here.
COPY app/ /app/
CMD [ "/run.sh" ]
