```table-of-contents
```
# Descending Order
## Question 1
**Given a list of numbers, order all numbers from largest to smallest using Query Syntax**

### Solution - Query Syntax
```cs
(from x in numbers
orderby x descending
select x
).Dump();
```

## Question 2
**Given a list of numbers, order all numbers from largest to smallest using Method Syntax**  
NOTE: Result type is IEnumerable\<Int32>

### Solution - Method Syntax
```cs
numbers.OrderByDescending(x => x)
.Select(x => x)
.Dump();
```
## Output
![[Pasted image 20240526010044.png|300]]


