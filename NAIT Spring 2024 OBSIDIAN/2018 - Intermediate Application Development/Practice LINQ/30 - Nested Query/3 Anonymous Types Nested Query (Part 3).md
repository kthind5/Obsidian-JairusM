```table-of-contents
```
# Question
**Given a list of Product, return the following information.**

- Product Name (shown as ProductName)
    
- Orders Detail (shown as Details)
    
    - Order ID
    - Customer Name (shown as Customer)
    - Order Date
    - Quantity Sold (shown as Sold)
- **Order Product Name and Quantity Descending**
    
- **We only want to see the following:**
    
    - **Products that have been sold in 2018**
    - **Only those Products that have been sold 40 or more**

# Solution
```cs
Products
  .OrderBy(x => x.ProductName)
  .Select(x => new
  {
  	ProductName = x.ProductName,
  	Details = OrderDetails
  		   .Where(od => od.ProductID ==x.ProductID
  					&& od.Order.OrderDate.Value.Year == 2018
  					&& od.Quantity >= 40)
  			.OrderByDescending(od => od.Quantity)			
  		.Select(od => new
  		{
  			OrderID = od.OrderID,
  			Customer = od.Order.Customer.CompanyName,
  			Sold = od.Quantity
  		})
  }).Dump();
```

# Output

![[Pasted image 20240526022644.png]]