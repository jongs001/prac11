# syntax=docker/dockerfile:1
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /app

ARG VERSION=0.4.254

# Copy csproj and restore as distinct layers
COPY . .

# Install dependencies
# Java (for Dependency Check)
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive \
    apt-get -y install default-jre-headless && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* 
# node / npm
RUN apt-get update && \
    apt-get install -y nodejs npm
# DevSkim
RUN dotnet tool install Microsoft.CST.DevSkim.CLI --version 0.4.254 --tool-path /bin
