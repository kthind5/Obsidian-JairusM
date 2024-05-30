```table-of-contents
```
# Question
**Given a list of Orders, return the following information.**

- Order ID
- Number of transaction that makes up that order (shown as TransactionCount)
- Largest transaction that that makes up that order [Quantity * UnitPrice] (shown as MaxExtPrice)
- Smallest transaction that that makes up that order [Quantity * UnitPrice] (shown as MinExtPrice)
- Average transaction that that makes up that order [Quantity * UnitPrice] (shown as AvgExtPrice)
- Calculate the Order sub total before discount [Quantity * UnitPrice] (shown as SubTotal)
- **Order by Order ID**

# Solution
```cs
Orders
  .Select(o => new
  {
  	OrderID = o.OrderID,
  	TransactionCount = o.OrderDetails.Count(),
  	MaxExtPrice = o.OrderDetails.Max(od => od.Quantity * od.UnitPrice),
  	MinExtPrice = o.OrderDetails.Select(od => od.Quantity * od.UnitPrice).Min(),
  	AvgExtPrice = o.OrderDetails.Average(od => od.Quantity * od.UnitPrice),
  	SubTotal = o.OrderDetails.Select(od => od.Quantity * od.UnitPrice).Sum()
  }).Dump();
```

# Output
![[Pasted image 20240526023937.png]]