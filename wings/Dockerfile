# Use a base image with Go pre-installed
FROM golang:alpine AS builder

WORKDIR /app

RUN apk update && apk add --no-cache git make
RUN git clone https://github.com/pterodactyl/wings.git
WORKDIR /app/wings

# Patch file the container
COPY plugins/modpack-installer/wings.patch .
RUN git apply wings.patch

# Build the Wings binary
RUN make build

# Create update the wings image with new binary
FROM ghcr.io/pterodactyl/wings:latest
COPY --from=builder /app/wings/build/wings_linux_amd64 /usr/bin/wings