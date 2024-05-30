```table-of-contents
```
# Question 1
**Given a list of Addresses, find all address where country is "Canada" and city is "Vancouver" using Query Syntax**

## Solution - Query Syntax
```cs
(from x in Addresses
where x.Country == "Canada"  && x.City == "Vancouver"
select x
).Dump();
```

# Question 2
**Given a list of Addresses, find all address where country is "Canada" and city is "Vancouver" using Method Syntax**

## Solution - Method Syntax
```cs
Addresses
.Where(x => x.Country == "Canada" && x.City == "Vancouver")
.OrderBy(x => x.City)
.Select(x => x)
.Dump();
```

# Output
![[Pasted image 20240526012206.png]]