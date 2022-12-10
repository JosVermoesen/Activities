# Activities

## Walking sceleton API

Creates the boilerplate for the projects and adds the references between them.

```powershell
dotnet tool list -g
Write-Host "About to Create the directory" -ForegroundColor Green

mkdir Activities
cd Activities

Write-Host "About to create the solution and projects" -ForegroundColor Green
dotnet new sln
dotnet new webapi -n API
dotnet new classlib -n Application
dotnet new classlib -n Domain
dotnet new classlib -n Persistence

Write-Host "Adding projects to the solution" -ForegroundColor Green
dotnet sln add API/API.csproj
dotnet sln add Application/Application.csproj
dotnet sln add Domain/Domain.csproj
dotnet sln add Persistence/Persistence.csproj

Write-Host "Adding project references" -ForegroundColor Green
cd API
dotnet add reference ../Application/Application.csproj
cd ../Application
dotnet add reference ../Domain/Domain.csproj
dotnet add reference ../Persistence/Persistence.csproj
cd ../Persistence
dotnet add reference ../Domain/Domain.csproj
cd ..

Write-Host "Executing dotnet restore" -ForegroundColor Green
dotnet restore

Write-Host "Finished!" -ForegroundColor Green
```

### Nugget Packages

#### Add the following packages to the Persistance project

- Microsoft.EntityFrameworkCoreSqlLite

#### Add the following packages to the API project

- Microsoft.EntityFrameworkCore.Design

### Install or update dotnet Entity Framework tool

```bash
dotnet tool list -g
```

#### First install

```bash
dotnet tool install --global dotnet-ef
```

#### Update EF to latest version dotnet core version

For example:

```bash
dotnet tool update -g dotnet-ef --version 7.0.0
```

#### Some EF commands

Use switches -s and -p to specify the startup project and the project where the migrations are located.

```bash
dotnet ef migrations add InitialCreate -s API -p Persistence
dotnet ef database update
```

## Walking sceleton REACT

Creates the boilerplate for the projects and adds the references between them.

```bash
npx create-react-app client-app --use-npm --template typescript
```

## Git

```bash
git status
```

### Initialize Git repository

```bash
git init
```

### Create dotnet gitignore

```bash
dotnet new gitignore
```
