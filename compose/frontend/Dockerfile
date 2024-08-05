# syntax=docker/dockerfile:1
FROM node:lts-alpine as base


# Update dependencies
RUN apk update \
    # Install git
    && apk add --no-cache openssh git curl \
    # Install nuxi package
    && corepack enable \
    && corepack prepare yarn@stable --activate \
    && yarn set version stable \
    && yarn config set --home enableTelemetry 0

# Set up the working directory
WORKDIR /app

# Specify the host variable
ENV HOST 0.0.0.0

EXPOSE 5173

FROM base as dev

# Set up the working directory
WORKDIR /app

# Run the Nuxt service
CMD ["yarn", "dev"]


