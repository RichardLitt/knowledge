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

### name = main

The `__name__ == '__main__'` Python idiom is used to ensure that a script is started only when the script is executed directly. Otherwise, it is skipped.
