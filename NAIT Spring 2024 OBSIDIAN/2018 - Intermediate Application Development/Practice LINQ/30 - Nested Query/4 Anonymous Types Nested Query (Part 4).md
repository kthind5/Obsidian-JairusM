```table-of-contents
```
# Question
**Given a list of Categories, return the following information.**

- Category Name (shown as CategoryName)
    
- Product Detail (shown as Details)
    
    - Product Name (shown as ProductName)
    - Total Quantity Sold (shown as TotalSold)
- **Order Category Name and Product Name**
    
- **NOTE: When getting the Total Quantity Sold, you will have to cast the Quantity as nullable. IE: (int?)x.Quantity**

# Solution
```cs
Categories
  .OrderBy(x => x.CategoryName)
  .Select(x => new
  {
  	CategoryName = x.CategoryName,
  	Details = Products
  				.Where(p => p.CategoryID == x.CategoryID)
  				.OrderBy(p => p.ProductName)
  				.Select(p => new
  				{
  					ProductName = p.ProductName,
  					TotalSold = p.OrderDetails.Sum(x => (int?)x.Quantity)
  				})
  })
  .Dump();
```

# Output
![[Pasted image 20240526022831.png]]