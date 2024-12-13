# Class attributes

> **TL;DR:**
> Try to avoid using mutable objects as class attributes.

A misconception that might happen is considering class attributes as attributes
of the instances. This becomes clear when the class attributes are mutable.

For example, let's define a class with a class attribute `x`, and an _instance_
attribute `y`:

```python
class My:
    x = [1, 2, 3]

    def __init__(self, y):
        self.y = y
```

```python
a = My([4, 5, 6])
b = My([7, 8, 9])
```

Both `a` and `b` have `x` and `y` attributes:

```python
print(a.x)
print(a.y)
```

```
[1, 2, 3]
[4, 5, 6]
```

```python
print(b.x)
print(b.y)
```

```
[1, 2, 3]
[7, 8, 9]
```

What if we change a value of `a.x`?

```python
a.x[-1] = 10
print(a.x)
```

```
[1, 2, 10]
```

Cool... but what happened in `b`?

```python
print(b.x)
```

```
[1, 2, 10]
```

😱 that was unexpected, right?

## Conclusion

Be careful when using mutable class attributes!
