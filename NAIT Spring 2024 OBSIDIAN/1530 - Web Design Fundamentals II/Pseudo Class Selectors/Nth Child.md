```table-of-contents
```
# nth-child()
Selects an element from a list of siblings
![[Pasted image 20240521202009.png]]

# nth-last-child()
This works the same as nth-child(), but it starts counting from the end of a list rather than the beginning of it.
Example:
![[Pasted image 20240521202109.png]]

# :first-child, :lastchild, & :only-child
## :first-child
This selects the frist element in a list of siblings

## :last-child
This selects the last element in a list of siblings

### Examples 
![[Pasted image 20240521202251.png]]

## :only-child
If there is an element without any siblings, it will get selected.
### Example
![[Pasted image 20240521202332.png]]

## :nth-of-type() & :nth-last-of-type
### nth-of-type(n)
Select an element amongst a group of siblings, based upon the order in which it appears.
#### Example
![[Pasted image 20240521202452.png]]
### :nth-last-of-type(n)
This is the same thing as nth-of-type, but it starts counting backwards from the end rather than the beginning.


## :first-of-type & :last-of-type
### first-of-type
Selects only the first element of its type in a group of sibling elements. If this elements is used multiple times, any subsequent times will be ignored (not selected).

### last-of-type
Selects only the last element of its type in a group of sibling elements. If this element is used multiple times, any prior times will be ignored (not selected).