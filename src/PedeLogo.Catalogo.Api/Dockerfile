#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base

EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build

COPY ["PedeLogo.Catalogo.Api/PedeLogo.Catalogo.Api.csproj", "PedeLogo.Catalogo.Api/"]
RUN dotnet restore "PedeLogo.Catalogo.Api/PedeLogo.Catalogo.Api.csproj"
COPY . .
RUN dotnet build "PedeLogo.Catalogo.Api/PedeLogo.Catalogo.Api.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "PedeLogo.Catalogo.Api/PedeLogo.Catalogo.Api.csproj" -c Release -o /app/publish

FROM base AS final

COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "PedeLogo.Catalogo.Api.dll"]