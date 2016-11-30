# Python

Some notes:

### Decorators

These are fun; basically, they're just syntactic sugar. See [this article](https://en.wikipedia.org/wiki/Python_syntax_and_semantics#Decorators).

```py
@viking_chorus
def menu_item():
    print("spam")
```

Is the same as:

```py
def menu_item():
    print("spam")
menu_item = viking_chorus(menu_item)
```
