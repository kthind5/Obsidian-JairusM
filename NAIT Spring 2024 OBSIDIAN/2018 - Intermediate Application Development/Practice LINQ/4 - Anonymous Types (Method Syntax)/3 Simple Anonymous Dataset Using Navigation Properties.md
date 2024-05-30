```table-of-contents
```
# Question
**Given a list of Customer, return the following information:**  

- Customer ID (shown as CustomerNo)
- Company Name (shown as Name)
- Contact Name
- Address
- City
- Country
- **Where the companies are in North America**
- **Order by Country, Company Name**

# Solution
```cs
Customers
.Where(x => x.Address.Country == "Canada"
  		|| x.Address.Country == "Mexico"
  		|| x.Address.Country == "USA")
  		
//  You can also use the ".Equals" method
//.Where(x => x.Address.Country.Equals("Canada")
//			|| x.Address.Country.Equals("Mexico")
//			|| x.Address.Country.Equals("USA"))

.OrderBy(x => x.Address.Country)
.ThenBy(x => x.CompanyName)
.Select(x => new
{
  CustomerNo = x.CustomerID,
  Name = x.CompanyName,
  ContactName = x.ContactName,
  Address = x.Address.Address,
  City = x.Address.City,
  Country = x.Address.Country
})
.Dump();
```


# Output
![[Pasted image 20240526012832.png]]