```table-of-contents
```
# Question 1 
**Given a list of Orders, return the following information.**
- Order ID
- Order Date
- Customer Name
- **Using Take, get the first 10 records**

## Solution
```cs
//  Using take on the order collection
Orders
//  order by must be done before take
.OrderBy(x => x.OrderID)
.Take(10)
.Select(x => new
{
  OrderID = x.OrderID,
  OrderDate = x.OrderDate,
  Customer = x.Customer.CompanyName
}).Dump();

//  Using take of the collection created from the select
Orders
//  order by must be done before take
.OrderBy(x => x.OrderID)
.Select(x => new
{
  OrderID = x.OrderID,
  OrderDate = x.OrderDate,
  Customer = x.Customer.CompanyName
})
.Take(10)
.Dump();
```

## Output
![[Pasted image 20240527185441.png]]


# Question 2
**Given a list of Orders, return the following information.**

- Order ID
- Order Date
- Customer Name
- **Using Skip and Take, Skip the first 5 records and Take the next 10**

## Solution
```cs
//  Using take on the order collection
Orders
//  order by must be done before take
.OrderBy(x => x.OrderID)
.Skip(5)
.Take(10)
.Select(x => new
{
  OrderID = x.OrderID,
  OrderDate = x.OrderDate,
  Customer = x.Customer.CompanyName
}).Dump();

//  Using take of the collection created from the select
Orders
//  order by must be done before take
.OrderBy(x => x.OrderID)
.Select(x => new
{
  OrderID = x.OrderID,
  OrderDate = x.OrderDate,
  Customer = x.Customer.CompanyName
})
.Skip(5)
.Take(10)
.Dump();
```
## Output
![[Pasted image 20240527185551.png]]

