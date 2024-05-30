```table-of-contents
```
# Question
**Given a list of Suppliers, return the following information.**

- Supplier Name (shown as Name)
    
- History
    
    - Products sold by the supplier (shown as name)
    - Total quantity sold to customer. They will used this information to figure out which is the best selling items (shown as QuantitySold)
- **Order by Suppliers then Quantity of items sold from largest to smallest, Name**

# Solution
```cs
void Main()
{
  Suppliers
  .OrderBy(s => s.CompanyName)
  .Select(s => new
  {
  	Name = s.CompanyName,
  	History = Products
  				.Where(p => p.SupplierID == s.SupplierID)
  				.Select(p => new HistoryView()
  				{
  					Name = p.ProductName,
  					QuantitySold = OrderDetails
  						.Where(od => od.ProductID == p.ProductID)
  						.Sum(od => od.Quantity)

  				}).OrderByDescending(x => x.QuantitySold)
  })
  .Dump();
}

public class HistoryView
{
  public string Name { get; set; }
  //  quantity sold must be nullable due to OrderDetails.Quantity being nullable
  public int? QuantitySold { get; set; }
}
```

# Output
![[Pasted image 20240526023900.png]]
