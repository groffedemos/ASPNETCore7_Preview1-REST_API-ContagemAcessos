FROM mcr.microsoft.com/dotnet/sdk:7.0.100-preview.1 AS build-env
WORKDIR /app

# Copiar csproj e restaurar dependencias
COPY *.csproj ./
RUN dotnet restore

# Build da aplicacao
COPY . ./
RUN dotnet publish -c Release -o out

# Build da imagem
FROM mcr.microsoft.com/dotnet/aspnet:7.0.0-preview.1
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "APIContagem.dll"]