```table-of-contents
```
# Question
**Given a list of Customer, return the following information as a strongly type list.**

- Customer ID (shown as CustomerId)
- Company Name (shown as Company)
- Contact Name (shown as Name)
- Contact Position (shown as Position)
- City
- Country
- **Where the companies are in North America**
- **Order by Country, Company Name**

**NOTE: The strongly type name will be CompanyView**

# Solution
```cs
void Main()
{
  Customers
  .Where(x => x.Address.Country == "Canada"
  			|| x.Address.Country == "Mexico"
  			|| x.Address.Country == "USA")
  .OrderBy(x => x.Address.Country)
  .ThenBy(x => x.CompanyName)
  .Select(x => new CompanyView()
  {
  	CustomerID = x.CustomerID,
  	Company = x.CompanyName,
  	Name = x.ContactName,
  	Position = x.Address.Address,
  	City = x.Address.City,
  	Country = x.Address.Country
  })
  .Dump();
}

public class CompanyView
{
  public string CustomerID { get; set; }
  public string Company { get; set; }
  public string Name { get; set; }
  public string Position { get; set; }
  public string City { get; set; }
  public string Country { get; set; }
}
```


# Output
![[Pasted image 20240526013258.png]]