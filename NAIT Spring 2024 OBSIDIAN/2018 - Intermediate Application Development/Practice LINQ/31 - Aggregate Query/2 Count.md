```table-of-contents
```
# Question
**Given a list of Suppliers, return the following information.**

- Supplier Name (shown as Name)
    
- Number of Products they supply (shown as ProductCount)
    
- **Order by Number of Products from largest to smallest, Name**

# Solution
```cs
Suppliers
.Select(s => new
{
  Name = s.CompanyName,
  ProductCount = Products
  			.Where(p => p.SupplierID == s.SupplierID)
  			.Count()
}).OrderByDescending(x => x.ProductCount)
.ThenBy(x => x.Name)
.Dump();
```

# Output
![[Pasted image 20240526023700.png|350]]