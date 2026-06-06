# Estágio de compilação
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copia o projeto usando caminhos relativos ao contexto
COPY ["MinhaApiCloud.csproj", "./"]
RUN dotnet restore "./MinhaApiCloud.csproj"

# Copia o resto dos arquivos da API
COPY . .
RUN dotnet publish "MinhaApiCloud.csproj" -c Release -o /app/publish

# Estágio de execução
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "MinhaApiCloud.dll"]