{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}

{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}

<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <packageSources>
    <clear />
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
  </packageSources>
  <fallbackPackageFolders>
    <clear />
  </fallbackPackageFolders>
</configuration>




using SCleanArchitecture.SimpleAPI.Application.Extensions;
using SCleanArchitecture.SimpleAPI.Infrastructure.Extentions;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container.

builder.Services.AddControllers();
// Learn more about configuring Swagger/OpenAPI at https://aka.ms/aspnetcore/swashbuckle
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();
builder.Services.AddApplicationServices();
builder.Services.AddInfrastructureServices();

var app = builder.Build();

// Configure the HTTP request pipeline.
// تفعيل Swagger في جميع البيئات (Development و Production)
app.UseSwagger();
app.UseSwaggerUI();

app.UseAuthorization();

app.MapControllers();

app.Run();

@SCleanArchitecture.SimpleAPI_HostAddress = http://localhost:5232

GET {{SCleanArchitecture.SimpleAPI_HostAddress}}/weatherforecast/
Accept: application/json

###

<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Mvc.Abstractions" Version="2.3.0" />
    <PackageReference Include="Swashbuckle.AspNetCore" Version="6.6.2" />
  </ItemGroup>

  <ItemGroup>
    <Folder Include="Infrastructure\Data\" />
  </ItemGroup>

</Project>

namespace SCleanArchitecture.SimpleAPI
{
    public class WeatherForecast
    {
        public DateOnly Date { get; set; }

        public int TemperatureC { get; set; }

        public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);

        public string? Summary { get; set; }
    }
}
