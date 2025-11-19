# worker/Dockerfile (Alpine version - smaller)
FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine AS build
WORKDIR /src
COPY Worker.csproj ./
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/runtime:7.0-alpine
WORKDIR /app
COPY --from=build /app .
CMD ["dotnet", "Worker.dll"]
