---
tags:
  - Csharp
  - HTML
  - Blazor
  - CPSC1517
  - front-end
  - back-end
---

Blazor is a C# framework for developing HTML webpages that can use both C# and html to create websites. This allows you to create dynamic elements in a website. 

A blazor page involves a .razor file. The razor file contains HTML and then either a separate file for C# or an @code section below it. To use something such as an if or a loop in Blazor, you can use an a @ with a for or an if. For example, you can do the following: 

```C#
@if (!string.IsNullOrWhiteSpace(receivedData))
{
	<p>This is a paragraph that only displays if the above is true, @receivedData</p>
}
```

## Where the C# goes
The above requires that you also need to define the variables below in the @code section like below: 

```C#
@code {
	private string receivedData;
}
```
You can also put the `@code` section in a different file so that you can work on it separately, found in [[2 Creating a blazor code file]]

---
## Navigation
Additionally, to setup navigation for the page, there is `Shared/NavMenu.razor` where you can add links to the side of the default Blazor page. To define the URL where you can access a blazor page, you must put the line `@page "/pageName"`, where you go to the Blazor site and navigate to pageName. 

## Learn Blazor
Some links to pages where you can learn Blazor: 
[MSDN Learn Blazor](https://learn.microsoft.com/en-us/aspnet/core/blazor)
[Blazor School](https://blazorschool.com/tutorial/blazor-server/dotnet7/introduction-926506)

## Cool things to know
* While you are in Visual Studio, you can: 
	* Press F1 to go find online help for whatever you have selected.
	* Press F12 to go to the code block where a variable is contained.
* You can format your Blazor page in bootstrap with [[bootstrap formatting]]

## Bootstrap formatting
You can also format using [[bootstrap formatting]] methods such as `col-md-4`, a 4 column in a row (see below)
![[images/Blazor Controls Screenshot with Bootstrap formatting.png]]
You can also embed entire pages in Blazor by putting `<filename>`, where the filename will be another razor page. When doing this, you can have a [[3 Callback event]]. 