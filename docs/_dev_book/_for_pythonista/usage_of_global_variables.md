## What is `global` keyword?
It is used to assign the value for the variable outside the scope

### Example 1
```
val = 10

def print_val():
    print(val)

print_val()
```
This should print
```
10
```

## But, if `val` to be changed
```
val = 10

def print_val():
    val = val + 12
    print(val)

print_val()
```
This will through the error
```
UnboundLocalError: local variable 'val' referenced before assignment
```