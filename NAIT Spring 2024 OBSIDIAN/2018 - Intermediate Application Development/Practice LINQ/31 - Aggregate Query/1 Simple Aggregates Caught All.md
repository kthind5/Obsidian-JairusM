```table-of-contents
```
# Question 
**Given a list of Products, return a single result.**

- Count
- Min Price
- Max Price
- Average Price
- Total Price (This is assuming that someone bought one of each thing.)
- **We only want to see those products that have are not discontinued**
- **NOTE: You will need to use the FirstOrDefault()**

# Solution
```cs
Products
  .Select(x => new
  {
  	Count = Products
  				.Where(x => x.Discontinued == false)
  				.Count(),
  	MinPrice = Products
  				.Where(x => x.Discontinued == false)
  				.Min(x => x.UnitPrice),
  	MaxPrice = Products
  				.Where(x => x.Discontinued == false)
  				.Select(x => x.UnitPrice).Max(),
  	AveragePrice = Products
  				.Where(x => x.Discontinued == false)
  				.Average(x => x.UnitPrice),
  	TotalPrice = Products
  				.Where(x => x.Discontinued == false)
  				.Select(x => x.UnitPrice).Sum()
  }
)
.FirstOrDefault()
.Dump();
```

# Output
![[Pasted image 20240526023601.png|300]]
