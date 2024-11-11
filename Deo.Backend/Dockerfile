FROM mcr.microsoft.com/dotnet/sdk:8.0-alpine3.20 AS builder


COPY . /app-build

WORKDIR /app-build

RUN dotnet restore --locked-mode && dotnet publish

#EXPOSE 6680

#ENTRYPOINT [ "dotnet", "run", "launch" ]

FROM mcr.microsoft.com/dotnet/aspnet:8.0-alpine3.20

WORKDIR /app

COPY --from=builder /app-build/bin/Release/net8.0/publish /app/

EXPOSE 8080

ENTRYPOINT [ "dotnet", "Deo.Backend.dll", "--urls", "http://*:8080"]