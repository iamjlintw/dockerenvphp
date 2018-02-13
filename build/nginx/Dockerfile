FROM 'nginx:alpine'
ARG DEV_GID
ARG DEV_UID
RUN echo "Build number: $DEV_GID $DEV_UID"
RUN addgroup -S -g $DEV_GID app
RUN adduser -G app -S -u $DEV_UID app