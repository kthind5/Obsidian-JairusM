```table-of-contents
```
# Database
`In this example it is Westwind`

# Question
**Given a list of Address, return the following information:**  

- Address ID
- Name
    - Use the ternary operator and the navigation property to get one of the following data values. You will also needs to use the .any aggregate
        - Customers -> CompanyName
        - Employees -> First & Last name
        - Orders -> ShipName
        - Suppliers -> CompanyName
        - Null values -> Unknown
- Address Type
    - Use the ternary operator and the navigation property to get one of the following data values
        - Customers -> Customer
        - Employees -> Employee
        - Orders -> Order
        - Suppliers -> Supplier
        - Null values -> Unknown
- Address
- City
- Region _(If the region is null then list it as "Unknown")_
- Country
- **Order by Country, Address ID**


# Solution
```cs
Addresses
.OrderBy(x => x.Country)
.ThenBy(x => x.AddressID)
.Select(x => new
{
  	Name = Customers.Any(c => c.AddressID == x.AddressID) 
  	? Customers.Where(c => c.AddressID == x.AddressID)
  		.Select(c => c.CompanyName).FirstOrDefault() 
  	: x.Employees.Any(e => e.AddressID == x.AddressID) 
  	? Employees.Where(e => e.AddressID == x.AddressID)
  		.Select(e => e.FirstName + " " + e.LastName).FirstOrDefault()
  	: Orders.Any(o => o.ShipAddressID == x.AddressID) 
  	? Orders.Where(o => o.ShipAddressID == x.AddressID)
  		.Select(o => o.ShipName).FirstOrDefault()
  	: Suppliers.Any(s => s.AddressID == x.AddressID)
  	? Suppliers.Where(s => s.AddressID == x.AddressID)
  		.Select(s => s.CompanyName).FirstOrDefault()
  	: "Unknown",
  AddressID = x.AddressID,
  AddressType = Customers.Any(c => c.AddressID == x.AddressID)
  	? "Customer"
  	: x.Employees.Any(e => e.AddressID == x.AddressID)
  	? "Employee"
  	: Orders.Any(o => o.ShipAddressID == x.AddressID)
  	? "Order"
  	: Suppliers.Any(s => s.AddressID == x.AddressID)
  	? "Supplier"
  	: "Unknown",
  Address = x.Address,
  City = x.City,
  Region = x.Region != null ? x.Region : "Unknown",
  Country = x.Country
}).Dump();
```


# Output
![[Pasted image 20240527185922.png]]
