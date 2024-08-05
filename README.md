# life-tracker

## Pre-requisites
1. Docker
2. Diesel CLI `RUN curl --proto '=https' --tlsv1.2 -LsSf https://github.com/diesel-rs/diesel/releases/download/v2.2.1/diesel_cli-installer.sh | sh`

## Setup
1. `docker compose build` 

## Run
1. `docker compose up`
2. `api` is running on `localhost:8000`

## run diesel
1. make sure the db is running (docker compose up postgres)
2. run `./utils/diesel ...args`