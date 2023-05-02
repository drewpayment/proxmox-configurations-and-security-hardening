FROM alpine:latest

# Updating the packages
RUN apk update && \
apk upgrade --available && sync

RUN apk install jq -y

WORKDIR /app

COPY cloudflare.sh /app/cloudflare.sh

RUN chmod +x /app/cloudflare.sh

RUN crontab -l | { cat; echo "*/5 * * * * /app/cloudflare.sh"; } | crontab -

# Run the command on container startup
CMD ["cron"]
