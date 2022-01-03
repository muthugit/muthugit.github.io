---
description: Encapsulation = wrapping the data
cover: ../.gitbook/assets/1_NfKsxc0DeQLDYOfltRNAXw (1).jpeg
coverY: 0
---

# Encapsulation in realtime

The OOPs the usage of encapsulation is very normal and easy. It is important to access the value of the variable through the function.

In the following simple example, we can get the value of `name` using `get_name()` function.

```python
class EncapsulationExample:
  def __init__(self):
    self.name = None
  
  def set_name(self, name):
    self.name = name
    
  def get_name(self):
    return self.name
```

The following example may explain one of the real time application of encapsulation&#x20;

```python
class EncapsulationExample:
  def __init__(self):
    self.name = None
  
  def set_name(self, name):
    name = f"{name} Updated"
    self.name = name
    
  def get_name(self, upper=False):
    if upper:
      self.name = self.name.upper()
    return self.name
```

In this example, both the `get` and `set` functions updating the original `self.name` variable



### Using @property to replace custom \`get\` and \`set\` functions

Usage example:
