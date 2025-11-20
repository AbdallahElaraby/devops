# worker/Dockerfile (Alpine version - smaller)
FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine AS build
WORKDIR /src
COPY Worker.csproj ./
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/runtime:7.0-alpine
RUN adduser -D -u 1000 appuser
WORKDIR /app
COPY --from=build /app .
RUN chown -R appuser:appuser /app
USER appuser
CMD ["dotnet", "Worker.dll"]
