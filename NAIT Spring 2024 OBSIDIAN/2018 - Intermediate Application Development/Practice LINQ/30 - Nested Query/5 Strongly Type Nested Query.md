```table-of-contents
```
# Question
**Given a list of Categories, return the following information.**

- Category Name (shown as Name)
- Description
- Items (_NOTE: We are using **Items** so not to cause confusion by calling it **Products**_)
    - Product Name (shown as Name)
    - Unit Price (shown as Price)
- **Order by Category Name, Product Name**

**NOTE: The strongly type name will be CategoryView & ProductView**

# Solution
```cs
void Main()
{
  Categories
  	.OrderBy(c => c.CategoryName)
  	.Select(c => new CategoryView()
  	{
  		Name = c.CategoryName,
  		Description = c.Description,
  		Products = Products
  					.Where(p => p.CategoryID == c.CategoryID)
  					.OrderBy(p => p.ProductName)
  					.Select(p => new ProductView()
  					{
  						Name = p.ProductName,
  						Price = p.UnitPrice
  					}
  					).ToList()
  	}).Dump();

}

public class CategoryView
{
  public string Name { get; set; }
  public string Description { get; set; }
  public List<ProductView> Products { get; set; }
}

public class ProductView
{
  public string Name { get; set; }
  public decimal Price { get; set; }
}
```

# Output
![[Pasted image 20240526022912.png]]