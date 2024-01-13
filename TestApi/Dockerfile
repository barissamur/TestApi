#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS build-env 
WORKDIR /app 


# csproj dosyasýný ve restore iþlemini çalýþtýr
COPY *.csproj ./
RUN dotnet restore

# Uygulama dosyalarýný kopyala
COPY . ./

# Uygulamayý build ve publish et
RUN dotnet publish -c Release -o out

# .NET Runtime Image kullanarak final ortamýný oluþtur
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build-env /app/out .

# Uygulamayý çalýþtýr
ENTRYPOINT ["dotnet", "TestApi.dll"]