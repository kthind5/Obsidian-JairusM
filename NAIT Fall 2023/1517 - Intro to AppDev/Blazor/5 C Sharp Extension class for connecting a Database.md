---
tags:
  - Csharp
  - CPSC1517
  - back-end
  - database
---
# Creating a C# Extension Class
This is to create a connection to a database with an extension and service class. You have to create an extension class that contains your service classes which contain your queries:
- Extension Class
	- Service Class 1
		- Query 1
		- Query 2
	- Service Class 2
		- Query 1
		- Query 2

1. Right click (somewhere?) add class
2. [[#Creating the extension class|Create extension class]]
3. [[#Make a service class|Make a service class for the extension class to use]]
4. [[#Making a query in the Service Class]]
5. [[#Register services in extension class]]
6. [[#Make the database connection]]

## Creating the extension class

```Csharp
public static class WestWindExtensions {
	//The extension method for this class below
	public static void WWExtensions (
		this IServiceCollection services,
		Action<DbContextOptionsBuilder> options
		) {
		
	}
}
```
The first argument registers all the services available for use by any systems to the library. Services will be coded in the BLL folder within individual classes. 
The second argument will register the database connection to be used by services requiring access to the database

To register the database connection, you can add the connection below: 
```csharp
//You have to add a using clause on something WestWind above
services.AddDbContext<WestWindContext>(options); //Put this inside the above extension
```

## Make a service class
You have to create another class, the `BuildVersionServices.BLL`, inside of the BLL folder. 
```csharp
namespace ClassWestWindSystem.BLL {
	public class BuildVersionServices {
		private readonly WestWindContext _context;
	}
}
```

Each method is a service. The service will need access to a `DbSet<T>` if accessing the database table. The `DbSet<T>` are located in the DbContext class which will be referenced by the variable _context. 

### Make a query in the Service Class

```csharp
public BuildVersion BuildVersion_GetVersion() {
	return _context.BuildVersions.FirstOrDefault();
}
```
This query is a query to get the build version of ???. By default, all records of the table will be returned. We will use LinQ queries to limit the return of the data. 
`.FirstOrDefault()` returns the first instance of a record that matches any given criteria or will return a null. 

## Register services in extension class
In the extension class, you have to add the code below to add the service class into the extension method:
```csharp
services.AddTransient<BuildVersionServices>( (serviceProvider) => {
	var context = serviceProvider.GetService<WestWindContext>();
	return new BuildVersionServices(context);
})
```
The first line retrieves the DbContext service Registration and the second one instantiates the class and supplies it. 

## Make the database connection
In your web application, you have the `appsettings.json`, where you can set attributes, such as allowed hosts or log level. Another option is connection strings, where you can determine where to connect to the database: 
```json
"ConnectionStrings": {
	"WWDB": "Server={ServerName};Database={DatabaseName};Trusted_Connection=true;MultipleActiveResultSets=true"
}
```
By putting it here, you can create multiple connections to different databases with different strings. 
Some issues you may run into: 
* An encryption issue can be solved by adding `encrypt=false` to the end of the connection string. 
* You may get a certificate error. This may happen because of a spelling mistake somewhere in here. 

---
To build the connection string in the program, you can write the following:
```csharp
var connectstring = builder.Configuration.GetConnectionString("WWDB");
```

You also have to setup the registration of services to be available for the web application. This example has the registration encapsulated within the class library within the extension class:
```csharp
builder.services.WWExtensions(options => options.UseSqlServer(connectionstring));
```
The connection string must be passed so that options in the extension class has it. 

## Add query to the Blazor page
Put this code inside of the code section for a [[1 Blazor introduction#Where the C goes|blazor page]] to trigger the query
```csharp
@using ClassWestWindSystem.BLL;
@using ClassWestWindSystem.Entities;
[Inject]
public BuildVersionServices _buildVersionServices { get; set; }
public BuildVersion buildVersion { get; set; }

protected override void OnInitialized() {
	buildVersion = _buildVersionServices.BuildVersion_GetVersion();
}

```
You have to do a dependency/property injection to insert your dependencies. Then you need a variable to receive the data, called `buildVersion` in this case.
Add this to the HTML segment of your page: 
```HTML
<p> </p>
```

