FROM mcr.microsoft.com/dotnet/sdk:8.0-alpine3.20 AS builder

WORKDIR /app-build

COPY . .

RUN dotnet restore --locked-mode && dotnet publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0-alpine3.20

WORKDIR /app

COPY --from=builder /app-build/bin/Release/net8.0/publish .

ENV ASPNETCORE_URLS=http://*:4000
EXPOSE 4000

#LABEL org.opencontainers.image.source=https://github.com/stadler-pascal/deo-webapp

ENTRYPOINT [ "/app/Deo.Frontend"]