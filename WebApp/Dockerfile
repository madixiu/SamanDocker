FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
RUN mkdir /app
WORKDIR /app
EXPOSE 5000
ENV ASPNETCORE_URLS=http://+:5000
#ENV ASPNETCORE_HTTPS_PORT=https://+:5001
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
RUN mkdir /src
WORKDIR /src
COPY ["SamanDocker.csproj", "."]
RUN dotnet restore "./SamanDocker.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "SamanDocker.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "SamanDocker.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "SamanDocker.dll"]