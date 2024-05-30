```table-of-contents
```
# Question 1
**Given a list of Addresses, find all address where country is "Canada" order by cities using Query Syntax**

## Solution - Query Syntax
```cs
(from x in Addresses
where x.Country == "Canada"
orderby x.City
select x
).Dump();
```


# Question 2
**Given a list of Addresses, find all address where country is "Canada" order by cities using Method Syntax**

## Solution - Method Syntax
```cs
Addresses
.Where(x => x.Country == "Canada")
.OrderBy(x => x.City)
.Select(x => x)
.Dump();
```

# Output
![[Pasted image 20240526012026.png]]
