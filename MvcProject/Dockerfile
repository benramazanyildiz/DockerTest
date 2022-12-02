#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["MvcProject/MvcProject.csproj", "MvcProject/"]
RUN dotnet restore "MvcProject/MvcProject.csproj"
COPY . .
WORKDIR "/src/MvcProject"
RUN dotnet build "MvcProject.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "MvcProject.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "MvcProject.dll"]


#FROM mcr.microsoft.com/dotnet/runtime:6.0 
#WORKDIR /app 
#COPY ["/bin/Release/net6.0/publish", "/app/"]
#ENTRYPOINT ["dotnet", "MvcProject.dll"]