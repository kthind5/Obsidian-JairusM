```table-of-contents
```
# Question 1
**Given a list of Addresses, find all addresses where address contains "Rd." order by country and then by city using Query Syntax**

## Solution - Query Syntax
```cs
(from x in Addresses
where x.Address.Contains("Rd.")
orderby x.Country, x.City
select x
).Dump();
```


# Question 2
**Given a list of Addresses, find all addresses where address contains "Rd." order by country and then by city using Method Syntax**

## Solution - Method Syntax
```cs
Addresses
.Where(x => x.Address.Contains("Rd."))
.OrderBy(x => x.Country)
.ThenBy(x => x.City)
.Select(x => x)
.Dump();
```


# Output
![[Pasted image 20240526012307.png]]
