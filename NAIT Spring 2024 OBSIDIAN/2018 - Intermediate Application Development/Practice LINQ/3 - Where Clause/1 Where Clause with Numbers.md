```table-of-contents
```
# Question 1
**Given a list of numbers, find all numbers that are less then 6, order from smallest to largest using Query Syntax** 

## Solution - Query Syntax
```cs
(from x in numbers
orderby x
select x
).Dump();
```

# Question 2 - Method Syntax
**Given a list of numbers, find all numbers that are less then 6, order from smallest to largest using Method Syntax**

## Solution
```cs
numbers
.OrderBy(x => x)
.Where(x => x < 6)
.Select(x => x)
.Dump();
```

# Output
![[Pasted image 20240526011839.png|300]]
