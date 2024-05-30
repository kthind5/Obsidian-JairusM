```table-of-contents
```
## Create your database connection string in the appsettings.json file

~~~c#
"ConnectionStrings": {
    "TWDB" : "Server=xxxx;Database=TrainWatch;Trusted_Connection=true;MultipleActiveResultSets=true"
  }
~~~
## Setup the service dependency registration for the web application
This will be done within your web application's `Program.cs` file. Use your in-class demonstration to complete this process. You will need to add a project reference to the web application pointing to the class library.

## Overview Query Page
[Link](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/blob/main/Exercise4/README.md#overview-query-page)
Create a `Query.razor`/`Query.razor.cs` Razor Page. The component class must declare in its dependency on the `RailCarTypeServices` and `RollingStockServices` classes using property injection. Details of the display can be found below. Be sure to add a menu item so that this page can be navigated to using the main menu (NavMenu); use the text "Query" for the link. Add an appropriate title to the page **and** the title of the browser tab.

The `Query` page will display summary information on the rolling stock data in an HTML table. Display the `ReportingMark`, `Owner`, `Capacity` and `InService` information. This query page will have two filters: Partial Search String and a Drop Down List (select control). The return query data will be of the same layout from both queries. Each filter will have its own `search` button requiring an event handler. Add a `Clear` button to reset both search arguments.

#### Partial Search String Filter
[Link](https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/blob/main/Exercise4/README.md#partial-search-string-filter)

Allow the user to enter a partial search string to filter on any portion of the reporting mark data (e.g.: "BN" or "50"). Present all of the records that have any of the partial data in the reporting mark in a table.

#### Drop Down List Filter
[Link]((https://github.com/CPSC-1517/Take-Home-Exercises-Sep-2023/blob/main/Exercise4/README.md#drop-down-list-filter)
Allow the user to pick a car type from a dropdown menu, and retrieve all of the cars of that type. Present all of the records of that car type in a table.

Only present the data columns as shown (in this sample) below:

|Reporting Mark|Owner|Capacity|InService|
|---|---|---|---|
|BN 19117|Burlington Northern|192200|True|
|BN 95782|Burlington Northern|192200|True|
|BN 95831|Burlington Northern|192200|True|
|BN 95887|Burlington Northern|192200|True|
|BN 95914|Burlington Northern|192200|True|

To ensure that your web application works, build and run your project.