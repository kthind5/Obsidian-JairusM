```C#
 public override string ToString()
    {
	 return $"{Title},{Level},{StartDate.ToString("MMM dd yyyy")},{Years}";
    }
```

or in our Train Exercises from Exercise 1

```c#
public override string ToString()
    {
    return $"{SerialNumber},{LightWeight},{Capacity},{LoadLimit},{Type},{Inservice}";
    }
```