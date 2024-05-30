```table-of-contents
```
# Order by Ascending
## Question 1
**Given a list of numbers, order all numbers using Query Syntax**  
NOTE: Result type is IOrderedEnumerable\<Int32>

### Solution - Query Syntax
```cs
(from x in numbers
orderby x
select x
).Dump();
```

## Question 2
**Given a list of numbers, order all numbers using Method Syntax**

### Solution - Method Syntax
```cs
numbers.OrderBy(x => x)
.Select(x => x)
.Dump();
```

## Output
![[Pasted image 20240526005954.png|300]]


