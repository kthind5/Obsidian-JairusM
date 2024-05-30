```table-of-contents
```
# Question
Anonymous Types Nested Query

**Given a list of Categories, return the following information.**

- Category Name (shown as Name)
- Description
- Items (_NOTE: We are using **Items** so not to cause confusion by calling it **Products**_)
    - Product Name (shown as Name)
    - Unit Price (shown as Price)
- **Order by Category Name, Product Name**

# Solution
```cs
void Main()
{
  Categories
  	.OrderBy(c => c.CategoryName)
  	.Select(c => new 
  	{
  		Name = c.CategoryName,
  		Description = c.Description,
  		Products = Products
  					.Where(p => p.CategoryID == c.CategoryID)
  					.OrderBy(p => p.ProductName)
  					.Select(p => new
  					{
  						Name = p.ProductName,
  						Price = p.UnitPrice
  					}
  					).ToList()
  	}).Dump();

}
```

# Output
![[Pasted image 20240526022511.png]]