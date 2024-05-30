```table-of-contents
```
# Question
**Given a list of Employees, return the following information:**  

- Employee ID (shown as CompanyId)
- First & Last Name (shown as FullName)
- Job Title (shown as Position)
- Hire Date (format as year/month/date) _No time value_
    - _You may need to google on how to do the date formatting_
- **Where the hire date is greater or equal to May 3, 2014**
    - _You will need to used the "Parse" function from the DateTime value type_
- **Order by last name**

# Solution
```cs
Employees
.Where(x => x.HireDate >= DateTime.Parse("05/03/2014"))
.OrderBy(x => x.LastName)
.Select(x => new
{
  EmployeeID = x.EmployeeID,
  FullName = x.FirstName + " " + x.LastName,
  Position = x.JobTitle,
  //  The @ symbol allows for you to escape the "/" character.  
  //	Otherwise you would need to a double "/"  IE:  {x.HireDate.Year}//{x.HireDate.Month}
  HireDate = $@"{x.HireDate.Year}/{x.HireDate.Month}/{x.HireDate.Day}"
})
.Dump();
```

# Output
![[Pasted image 20240526012637.png|500]]