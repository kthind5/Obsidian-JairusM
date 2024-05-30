```table-of-contents
```
# Question 
**Given 2 Customer (Bergs & Hungo), return the following information.**

- Category
- Product Name (show as Name)
- **Order by Category and Product Name**
- **We only want to see the following:**
    - **Those products that were purchase by both customers**

# Solution
```cs
void Main()
{
  //  get products used by Bergs
  var customer1 =
  	OrderDetails
  		.Where(x => x.Order.Customer.CustomerID.Equals("BERGS"))
  		.Select(x => new
  		{
  			ProductID = x.ProductID,
  			Product = x.Product.ProductName,
  			Category = x.Product.Category.CategoryName
  		}
  		)
  		.Distinct()
  		.OrderBy(x => x.ProductID);
  
  //  get products used by Hungo
  var customer2 =
  	OrderDetails
  		.Where(x => x.Order.Customer.CustomerID.Equals("HUNGO"))
  		.Select(x => new
  		{
  			ProductID = x.ProductID,
  			Product = x.Product.ProductName,
  			Category = x.Product.Category.CategoryName
  		}
  		)
  		.Distinct()
  		.OrderBy(x => x.ProductID);


  //  get all product that Bergs uses that is also used by Hungo
  customer1
  .Where(c1 => customer2.Any(c2 => c2.ProductID == c1.ProductID))
  .Select(x => new
  {
  	Category = x.Category,
  	Product = x.Product
  })
  		.OrderBy(x => x.Category)
  		.ThenBy(x => x.Product)
  		.Dump();
}
```

# Output
![[Pasted image 20240527185636.png|400]]