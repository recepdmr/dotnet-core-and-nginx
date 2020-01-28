FROM mcr.microsoft.com/dotnet/core/sdk:3.1


WORKDIR /app/test-nginx

COPY ./TestNginx/*.csproj .

RUN dotnet restore

COPY ./TestNginx ./

RUN dotnet publish  -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1

WORKDIR /app/test-nginx

COPY --from=build /app/test-nginx/out .

ENV ASPNETCORE_URLS http://*:5000

ENTRYPOINT [ "dotnet","TestNginx.dll" ]