
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY ["MinhaApiCloud.csproj", "./"]
RUN dotnet restore "./MinhaApiCloud.csproj"
COPY . .
RUN dotnet publish "MinhaApiCloud.csproj" -c Release -o /app/publish


FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ApiCloud.dll"]