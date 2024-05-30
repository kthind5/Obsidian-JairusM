---
tags:
  - Blazor
  - Csharp
  - back-end
  - CPSC1517
---
 ```table-of-contents
```
# Notes
Normally if you were using an injection method on your page, the method would look more like `_regionServices.Region_GetList`. If using Blazor, you would have something to process and then display the results. 

A Linqpad command you can use is `.Dump()` that you can execute on a variable to display it in the Linqpad results. 

# Putting it into your Visual Studio Project
When creating a query in LinQPad, you must use the plural of an entity, while inside of Visual Studio, you must use the singular. For example, you will have to change: 
`List<Regions>` to `List<Region>`
You will also have to add `_context` when you put it into the service class (see below)
![[5 C Sharp Extension class for connecting a Database#Make a query in the Service Class]]


# Final Code
![[Final Code]]


hello