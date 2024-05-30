```table-of-contents
```
# Then By Ordering Using Northwind Addresses Table
## Question 1
**Given a list of Addresses, order all address by country then city using Query Syntax**

### Solution - Query Syntax
```cs
(from x in Addresses
orderby x.Country,x.City
select x
).Dump();
```

## Question 2 
**Given a list of Addresses, order all address by country then city using Method Syntax**

### Solution
```cs
Addresses
.OrderBy(x => x.Country)
.ThenBy(x => x.City)
.Select(x => x)
.Dump();
```

## Output
![[Pasted image 20240526010446.png]]

