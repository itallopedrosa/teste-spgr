######################
# Build
FROM mcr.microsoft.com/dotnet/sdk:3.1

RUN apt-get update \
 && apt-get install -y nodejs npm --no-install-recommends \
 && npm i npm@latest -g

COPY src/ src/
WORKDIR src/

RUN dotnet build --configuration Release
RUN dotnet publish --configuration Release

######################
# Deploy
FROM mcr.microsoft.com/dotnet/aspnet:3.1

COPY deploy /app
WORKDIR /app

# WebApi
COPY  /deploy/WebApi /app/api/
# ApiGateway
COPY /deploy/ApiGateway /app/gateway/
# WebApp
COPY /deploy/WebApp /app/app/
