```table-of-contents
```
# Question
**Given a list of Order, return the following information.**

- OrderID
- Order Date (shown as OrderDate) _NOTE: When creating the property in the view, the DateTime is **nullable** (Please reference by to 1517)_
- Customer Name (shown as CustomerName)
- Contact Name (shown as ContactName)
- Details
    - Product Name (shown as Name)
    - Quantity
    - Unit Price (shown as Price)
    - Extend Price (shown as LineTotal)
- **Order by Customer Name, Product Name**
- **We only want to see those orders that were in May of 2018**

**NOTE: The strongly type name must end in View ie: XxxxView**

# Solution
```cs
void Main()
{
  Orders
  	.Where(o => o.OrderDate.Value.Month == 5 &&
  			o.OrderDate.Value.Year == 2018)
  	.OrderBy(o => o.Customer.CompanyName)
  	.Select(o => new OrderView()
  	{
  		OrderID = o.OrderID,
  		OrderDate = o.OrderDate,
  		CustomerName = o.Customer.CompanyName,
  		ContactName = o.Customer.ContactName,
  		Details = OrderDetails
  					.Where(od => od.OrderID == o.OrderID)
  					.OrderBy(od => od.Product.ProductName)
  					.Select(od => new OrderDetailView()
  					{
  						Name = od.Product.ProductName,
  						Quantity = od.Quantity,
  						Price = od.UnitPrice,
  						LineTotal = (od.Quantity * od.UnitPrice)
  					}).ToList()

  	}).Dump();
}

public class OrderView
{
  public int OrderID { get; set; }
  public DateTime? OrderDate { get; set; }
  public string CustomerName { get; set; }
  public string ContactName { get; set; }
  public List<OrderDetailView> Details { get; set; }
}

public class OrderDetailView
{
  public string Name { get; set; }
  public int Quantity { get; set; }
  public decimal Price { get; set; }
  public decimal LineTotal { get; set; }
}
```

# Output
![[Pasted image 20240526023005.png]]