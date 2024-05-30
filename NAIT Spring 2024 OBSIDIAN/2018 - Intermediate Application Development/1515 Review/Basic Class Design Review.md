```table-of-contents
```
# Code
```Csharp
class Sphere
{
	"example of Data Members"
	int x;
	int y;
	static int radius; // static means that it is shared
	
	const int minValue = 0;
	const int maxValue = 799;
	
	///example of Properties
	public Colour {get; private set;} // this is an auto implemented property
	
	public x {get; {return x;}} 
		set{ 
			if(value<=maxValue && value >= minValue)
				{
				x = value;
				} 
			else 
				{
					throw new Exception ("message")
				}
			} // manually implemented with own logic
		}
	
	static int FuncName (Unit left, Unit right)
	{
		left.x.CompareTo(right.X);
	}

	public override bool Equals(object obj)
	{
		if (!(obj is sphere arg))
			{
				return false;
			}
		else
			{
				return x.Equals(arg.x) && y.Equals(arg.y);	
			}
	} 
	List<Sphere> myList = newList<Sphere>();
	
	myList[3].x = 5;
	myList[3].Radius = 10; // This makes it so that only the Sphere in the index of 3 change the radius
	
	Sphere.Radius = 10; // This makes it so that ALL spheres in the list change the radius

	myList.Sort(Sphere.FuncName);

	myList.Sort((left,right) => right.Colour.ToRGB().CompareTo(left.Colour.ToRGB)));

	myList.OrderBy(x => x,y).ToList();

}
```

# Definitions
>[!info]
>**Delegate**:
>"A delegate is an object that can refer to a method. Thus, when we create a delegate, we are creating an object that can hold a reference to a method. Furthermore, the method can be called through this reference. Thus, a delegate can invoke the method to which it refers. The principal advantage of a delegate is that it allows us to specify a call to a method, but the method actually invoked is determined at runtime, not at compile time." 

```C#
delegate void delMyDelegate(object o);

private void MethodToExecute1(object o)
{
    // do something with object
}

private void MethodToExecute2(object o)
{
    // do something else with object
}

private void DoSomethingToList(delMyDelegate methodToRun)
{
    foreach(object o in myList)
        methodToRun.Invoke(o);
}

public void ApplyMethodsToList()
{
    DoSomethingToList(MethodToExecute1);
    DoSomethingToList(MethodToExecute2);
}
```
>[Source](https://stackoverflow.com/questions/2044301/what-is-delegate)

