```table-of-contents
```
# Question 
**Given a list of Employees, return the following information:**  

- Employee ID (shown as CompanyId) _Note: Company ID is how the company reference their employee ID_
- First Name (shown as Name)
- Last Name (shown as Surname)
- Job Title (shown as Position)
- **Order by last name**

# Solution
```cs
Employees
.OrderBy(x => x.LastName)
.Select(x => new
{
  CompanyId = x.EmployeeID,
  Name = x.FirstName,
  Surname = x.LastName,
  Position = x.JobTitle
})
.Dump();
```

# Output
![[Pasted image 20240526012507.png|500]]