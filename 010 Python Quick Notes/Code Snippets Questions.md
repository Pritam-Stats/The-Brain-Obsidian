#### What will the output of the following code snippet?
```Python
def outer():
	x = 10
	def inner():
		nonlocal x
		x += 10
		return x
	return inner

cl = outer()
print(cl())
print(cl())
```
- `nonlocal` allows the inner function to modify the variable of the outer function.
- Note, the outer function is returning a function address.
#### In python what does the `else` statement do when used with a loop?
It executes after the loop completes without a break.
```Python
i = 0
while i<10:
	print(i, end=" ")
	i += 1
else:
	print(10)
```
- Output- `0 1 2 3 4 5 6 7 8 9 10`

```Python
for i in range(11, 20):
	print(i, end=" ")
else:
	print(9)
```
- Output- `11 12 13 14 15 16 17 18 19 9`
So in both cases the else statement will execute. Only if we add a `break` statement inside the loop the `else` statement will not execute.