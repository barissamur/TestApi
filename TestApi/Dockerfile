# SDK Image kullanarak build ortam�n� olu�tur
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env
WORKDIR /app

# csproj dosyas�n� ve restore i�lemini �al��t�r
COPY *.csproj ./
RUN dotnet restore

# Uygulama dosyalar�n� kopyala
COPY . ./

# Uygulamay� build ve publish et
RUN dotnet publish -c Release -o out

# Runtime Image kullanarak final ortam�n� olu�tur
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build-env /app/out .












# Uygulamay� �al��t�r
# Uygulaman�z�n ad� TestApi.dll ise bu k�sm� de�i�tirmeyin, e�er farkl�ysa do�ru ad� girin.
ENTRYPOINT ["dotnet", "TestApi.dll"]





