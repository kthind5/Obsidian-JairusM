```table-of-contents
```
# Code Setup
```cs
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };
```

# Question 1
Given a list of numbers, select all numbers using Query Syntax

## Solution - Query Syntax
```cs
(from x in numbers
select x).Dump();
```


# Question 2 
Given a list of numbers, select all numbers using Method Syntax
## Solution
```cs
numbers.Select(x => x).Dump();
```

# Output

![[Pasted image 20240526004755.png|Output|300]]
