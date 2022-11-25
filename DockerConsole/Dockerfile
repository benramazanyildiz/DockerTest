#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

##FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base  #işletim sistemi ve uygun runtime yüklemesi yapılır docker hubtan 1.katman
##WORKDIR /app  #Projenin hangi folder içinde olacagý belirlenir. 2.katman bu katmanlarýn birleþimi imageyi olusturur
###copy dockerfile nerede ise oradan dosya yolu belirtilir bir boþluk býrakýlýp nereye kopyalacaksak o folder adý yazaýlýr.  COPY bin/reale/etx /app
##FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
##WORKDIR /src
##COPY ["DockerConsole/DockerConsole.csproj", "DockerConsole/"]
##RUN dotnet restore "DockerConsole/DockerConsole.csproj"
##COPY . .
##WORKDIR "/src/DockerConsole"
##RUN dotnet build "DockerConsole.csproj" -c Release -o /app/build

##FROM build AS publish
##RUN dotnet publish "DockerConsole.csproj" -c Release -o /app/publish /p:UseAppHost=false

##FROM base AS final
##WORKDIR /app
##COPY --from=publish /app/publish .
##ENTRYPOINT ["dotnet", "DockerConsole.dll"] #bir imageden bir container ayaga kalktıgında çalışacak olan kodu belirtiriz



FROM mcr.microsoft.com/dotnet/runtime:6.0 
WORKDIR /app 
COPY ["/bin/Debug/net6.0", "/app/"]
ENTRYPOINT ["dotnet", "DockerConsole.dll"]