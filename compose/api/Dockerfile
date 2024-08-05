FROM rust:latest as base

# Create the default user
RUN adduser --disabled-password --gecos "" default

# Set up UID and GID arguments
ARG UID=1000
ARG GID=1000
ENV UID $UID
ENV GID $GID

# Update the default user's UID and GID
RUN usermod -u $UID default && groupmod -g $GID default

# Create the /project_name directory before switching users
RUN mkdir /app && chown -R $UID:$GID /app

# Change ownership of the home directory
RUN chown -R $UID:$GID /home/default/

# Switch to the default user
USER default

# Set the working directory
WORKDIR /app

# Copy the project files
COPY ./services/api .

# Expose the application port
EXPOSE 8000

# Install diesel CLI
RUN curl --proto '=https' --tlsv1.2 -LsSf https://github.com/diesel-rs/diesel/releases/download/v2.2.1/diesel_cli-installer.sh | sh

# Define the development stage
FROM base as dev
CMD ["cargo", "run"]

# Define the production stage
FROM base as prod
RUN cargo build --release
CMD ["target/release/hello_rocket"]