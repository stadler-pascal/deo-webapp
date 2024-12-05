FROM mcr.microsoft.com/dotnet/sdk:8.0-alpine3.20 AS builder

WORKDIR /app-build

COPY . .

RUN dotnet restore --locked-mode && dotnet publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0-alpine3.20

WORKDIR /app

COPY --from=builder /app-build/bin/Release/net8.0/publish .

ENV ASPNETCORE_URLS=http://*:4000
EXPOSE 4000

ENTRYPOINT [ "/app/Deo.Frontend"]