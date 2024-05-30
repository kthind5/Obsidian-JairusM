```table-of-contents
```
# Question
**Given a list of Suppliers, return the following information.**

- Supplier Name (shown as Name)
- Contact Name
- City
- Items (_NOTE: We are using **Items** so not to cause confusion by calling it **Products**_)
    - Product Name (shown as Name)
    - Unit Price (shown as Price)
- **Order by Category Name, Product Price from largest to smallest**
- **We only want to see those products that have a value less than $10.00**

# Solution
```cs
void Main()
{
  Suppliers		
  	.OrderBy(s => s.CompanyName)
  	.Select(s => new
  	{
  		Name = s.CompanyName,
  		ContactName = s.ContactName,
  		City = s.Address.City,
  		Items = Products
  			.Where(p => p.UnitPrice < 10)
  			.OrderByDescending(p => p.UnitPrice)
  			.Select(p => new
  			{
  				Name = p.ProductName,
  				Price = p.UnitPrice
  			})
  
  	}).Dump();
}
```

# Output
![[Pasted image 20240526022603.png]]