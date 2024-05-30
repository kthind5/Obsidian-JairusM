```table-of-contents
```
# Database
`In this example it is Westwind`

# Setup 
`Use C# Statement and/or C# Program`

# Question
**Given a list of Payments, return the following information.**
- Payment Date (shown as Year)
- Payment Date (shown as Month)
- Payment Description (Payment)
- Total Payment (shown as Count)
- **Order Year, Month, Payment Description**
- **We want to group the information by Year, Month and then Payment Description**


# Solution
```cs
Payments
.GroupBy(p => new { p.PaymentDate.Year, p.PaymentDate.Month, p.PaymentType.PaymentTypeDescription })
.OrderBy(p => p.Key.Year)
.ThenBy(p => p.Key.Month)
.ThenBy(p => p.Key.PaymentTypeDescription)
.Select(p => new
{
  Year = p.Key.Year,
  Month = p.Key.Month,
  Payment = p.Key.PaymentTypeDescription,
  Count = p.Count()
}).Dump();
```

# Output
![[Pasted image 20240527185115.png|400]]
