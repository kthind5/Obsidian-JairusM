```table-of-contents
```
# Question
**Given a list of Payment Types, return the following information as a strongly type list.**

- Payment Type ID (shown as PaymentTypeID)
- Description (shown as Description)

**NOTE: The strongly type name will be PaymentTypeView**

# Solution
```cs
void Main()
{
  PaymentTypes
  .Select(x => new PaymentTypeView()
  {
  	PaymentTypeID = x.PaymentTypeID,
  	Description = x.PaymentTypeDescription
  })
  .Dump();
}

public class PaymentTypeView
{
  public int PaymentTypeID { get; set; }
  public string Description { get; set; }	
}
```

# Output
![[Pasted image 20240526013155.png|500]]
