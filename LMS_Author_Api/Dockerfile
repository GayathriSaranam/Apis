#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.


FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS build-env
WORKDIR /app
#Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore
#Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

#Build runtime image
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "LMS_Author_Api.dll"]