```table-of-contents
```
# Then By Ordering (property 1 then by property 2)
## Question 1
**Given a list of digits, order all digits by word length then alphabetical using Query Syntax**

### Solution - Query Syntax
```cs
(from x in digits
orderby x.Length, x
select x
).Dump();
```

## Question 2
**Given a list of digits, order all digits by word length then alphabetical using Method Syntax**  
NOTE: Result type is IEnumerable\<String>

### Solution - Method Syntax
```cs
digits
.OrderBy(x => x.Length)
.ThenBy(x => x)
.Select(x => x)
.Dump();
```

## Output
![[Pasted image 20240526010222.png|300]]


