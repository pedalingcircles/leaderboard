FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-buster AS build
WORKDIR /src
COPY ["WebEmpty/WebEmpty.csproj", "WebEmpty/"]
RUN dotnet restore "WebEmpty/WebEmpty.csproj"
COPY . .
WORKDIR "/src/WebEmpty"
RUN dotnet build "WebEmpty.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebEmpty.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebEmpty.dll"]