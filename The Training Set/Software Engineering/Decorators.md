A decorator is a function that is like an add-on to an existing function. It adds functionality without modifying its base behavior.
For example:

```python
def decorator(f): #These are like Haageslaag on Breads / Takes function f as argument
    def new_function():
        print("Extra Functionality")
        f()
    return new_function

@decorator #When defined like this, it takes the initial_function() as f()
def initial_function():
    print("Initial Functionality")

initial_function()
```


## Inbuilt decorators

### @property
@property is a built-in decorator for the [property()](https://docs.python.org/3/library/functions.html#property) function in Python. It is used to give "special" functionality to certain methods to make them act as getters, setters, or deleters when we define properties in a class.
```python
class House:

    def __init__(self, price):
        self._price = price

    @property
    def price(self):
        return self._price

    @price.setter
    def price(self, new_price):
        if new_price > 0 and isinstance(new_price, float):
            self._price = new_price
        else:
            print("Please enter a valid price")

    @price.deleter
    def price(self):
        del self._price
```

We can use them partially too, like only setter or only getters 
