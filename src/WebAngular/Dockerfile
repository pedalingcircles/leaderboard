FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-buster-slim AS base
# Setup NodeJs
RUN apt-get update && \
    apt-get install -y wget && \
    apt-get install -y gnupg2 && \
    wget -qO- https://deb.nodesource.com/setup_10.x | bash - && \
    apt-get install -y build-essential nodejs
# End setup
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-buster AS build
WORKDIR /src
COPY ["WebAngular/WebAngular.csproj", "WebAngular/"]
RUN dotnet restore "WebAngular/WebAngular.csproj"
COPY . .
WORKDIR "/src/WebAngular"
RUN dotnet build "WebAngular.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebAngular.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebAngular.dll"]