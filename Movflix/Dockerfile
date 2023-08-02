FROM mcr.microsoft.com/dotnet/sdk:6.0 AS base
WORKDIR /Movflix

# Copy everything
COPY . ./
# Restore as distinct layers
RUN dotnet restore
# Build and publish a release
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /Movflix
COPY --from=base /Movflix/out .
ENTRYPOINT ["dotnet", "Movflix.dll"]