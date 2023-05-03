FROM alpine:latest

# Updating the packages
RUN apk update && \
apk upgrade --available && sync

RUN apk add --no-cache jq bind-tools curl bash

WORKDIR /app

COPY cloudflare.sh /app/cloudflare.sh

RUN chmod +x /app/cloudflare.sh

RUN crontab -l | { cat; echo "*/5 * * * * /app/cloudflare.sh"; } | crontab -
RUN bash

# Run the command on container startup
CMD ["crond", "-f", "-d", "8"]
