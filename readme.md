# Publicar

## Azure ARM
	az login
	az group create --name rg-techchallenge2-dev --location eastus2
	az group deployment create --name Techchallenge2Deployment --resource-group rg-techchallenge2-dev --template-file ./template.json --parameters storageAccountName=sttechchallenge2dev sqlServerName=sqldb-techchallenge2-dev sqlDatabaseName=dbTechChallenge2 webAppName=app-techchallenge2 apiAppName=app-techchallenge2

## Configuração AzureSql
	- https://learn.microsoft.com/en-us/azure/azure-sql/database/network-access-controls-overview?view=azuresql#allow-azure-services

## Metodo Usado de publicação
	- Download do publish profile e realizado publish via visual studio

## StorageAccount
	### Alterar AzureBlobStorage.StorageConnectionString:
		az storage account show-connection-string --name sttechchallenge2dev --resource-group rg-techchallenge2-dev --output tsv
	### Criar um container e alterar no appsettings AzureBlobStorage.BlobContainerName do projeto Blog.Web 

# Editar Projeto

## Criar Migrations
	dotnet ef migrations add {Name} -c AppIdentityDbContext --project .\Infrastructure\Infrastructure.csproj --startup-project .\Api\Api.csproj --output-dir .\Identity\Migrations
	dotnet ef migrations add {Name} -c BlogContext --project .\Infrastructure\Infrastructure.csproj --startup-project .\Api\Api.csproj --output-dir .\Data\Migrations\BlogDb

# Referências

- https://learn.microsoft.com/en-us/cli/azure/
- https://github.com/dotnet-architecture/eShopOnWeb
- https://learn.microsoft.com/pt-br/aspnet/core/security/authentication/identity?view=aspnetcore-7.0&tabs=visual-studio
- https://github.com/ardalis/CleanArchitecture
- https://learn.microsoft.com/en-us/aspnet/core/blazor/?view=aspnetcore-7.0#blazor-server
- https://www.mudblazor.com/docs/overview
- https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming
