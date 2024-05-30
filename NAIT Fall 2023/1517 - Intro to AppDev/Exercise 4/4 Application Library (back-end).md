~~~table-of-contents

~~~
## Add Class Library
Add a Class library that supports .Net Core or .Net Standard to your solution called `TrainWatchSystem`. Use .Net Core 7 as your framework. Add 3 subfolders to this project: BLL, DAL, and Entities. _Remember that Github does not track empty folders, so you might wish to add a dummy.txt file in each folder if you intend to commit and push at this time. You can remove these dummy files as you add other files to the folder._

## Entity Framework (NuGet Packages)
We will be using the **Microsoft.EntityFrameworkCore.SqlServer lastest version** and **Microsoft.EntityFrameworkCore lastest version** NuGet packages to connect/interact to/with this database. Add these NuGet packages to the class library project. You will also need to add the NuGet packages to your web application project.

## Entities
You will use reverse engineering to create your entity classes that map to the database. This may be complted via EF Core Power Tools (EF Core verion is EF Core 7) or via CLI.

- If done via CLI, install the **Microsoft.EntityFrameworkCore.Design lastest version** NuGet package and complete the scaffolding as demonstrated by your instructor.
- If done via EF Core Power Tools, select all tables and take the default Context name and namespace. Place the entity classes in your Entities folder and the context class in your DAL folder.

[![ERD](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/raw/main/Exercise4/TrainWatch.png)](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/blob/main/Exercise4/TrainWatch.png)

The system should add a default namespace to your entity classes. Check it is the of follows: `namespace TrainWatchSystem.Entities`.

## DAL Context
In the "DAL" folder, a file called `TrainWatchContext.cs` was created which will contain the `TrainWatchContext` class. Ensure it inherits from `DbContext`. Your class should have a constructor for DbContextOptions<> options injection. Change the access level of the context class to **internal**. Your DbSet properties for your entity classes should also be present.


## Extension Class Creation

> [!Notes]
>**Your instructor may demonstrate a different technique in registering your services. Use the technique demonstrated by your instructor.** [Link]((https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/blob/main/Exercise4/README.md#your-instructor-may-demonstrate-a-different-technique-in-registering-your-services-use-the-technique-demonstrated-by-your-instructor))

The extension method will contain the dbcontext and transient services that will be available for dependency injection in your web application. This method will be called in the web application's `Program.cs`. The extension method will add your DbContext option and add the services (methods) of your BLL class (see below).

Create a class called `TrainWatchExtensions` at the root of the application library. Change the class to be public static.

Add the static method `TrainWatchDependencies`. Check your in-class demo for appropriate parameters. Within the method, you will register your DbContext and the AddTransient factory for your BLL service classes.

As you code, you will need to resolve references to needed namespaces holding your context class and service classes. 


## BLL Services
Each service class will need an appropriate internal constructor that requires an instance of the `TrainWatchContext` as a parameter. Save the parameter value into a private readonly variable. As you code, you will need to resolve references to needed namespaces holding your context class and entity class. Once you have created the class, register the class in your extension method via **AddTransient**. If a method has a parameter, ensure one was passed and if not throw an `ArgumentNullException`.


### TrainWatchServices
In this class, create a public method called `GetDbVersion()` that has no parameters and returns an instance of the `DbVersion` entity. The related database table should only have one row, so you can return that first item from the database context.


### RailCarType Services
In this class, create a public method called `GetRailCarTypes()` that has no parameters and returns a ordered collection of all records of the RailCarTypes entity.

### RollingStock Services
In this class, create a public method called `GetStockByReportMark(string)` that has one parameter and returns a collection of all RollingStock records where the ReportMark contains the parameter value. The parameter value will be a partial ReportMark. 

In this class, create a public method called `GetStockByCarType(int)` that has one parameter and returns a collection of all RollingStock records where the RailCarType matches the parameter value.

Rebuild your Application Class Library. You should get a successful build.

[[5 Web Application|Web Application]]