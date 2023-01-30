# Scope

Python is a powerful, high-level programming language that is widely used in a variety of applications. One of the key features of Python is its scope, which determines the lifetime and accessibility of variables, functions, and other objects within a program. In this article, we will explore the basics of Python scope and how it differs from other programming languages, as well as some common pitfalls to watch out for when working with scope in Python.

#### What is scope in programming?

In programming, scope refers to the portion of a program where a variable, function, or other object can be accessed or used. In other words, it defines the visibility and lifetime of a variable or function within a program. Variables and functions can have either global or local scope.

A variable or function with global scope is defined outside of any function or class and is accessible throughout the entire program. On the other hand, a variable or function with local scope is defined inside a function or class and is only accessible within that specific function or class.

#### How does scope work in Python?

In Python, scope works in a hierarchical manner, known as the LEGB rule (Local, Enclosing, Global, Built-in). When a variable is accessed, Python will first look for the variable in the local scope, then in the enclosing scope (i.e. any containing function or class), then in the global scope, and finally in the built-in scope. If the variable is not found in any of these scopes, a NameError is raised.

For example, consider the following code:

```python
x = 1  # global scope

def my_function():
    x = 2  # local scope
    print(x)

my_function()  # prints 2
print(x)  # prints 1
```

In the above code, we have a global variable `x` with a value of 1, and a local variable `x` within the `my_function` function with a value of 2. When the `my_function` is called, the local variable `x` is accessed and the value 2 is printed. Outside of the function, the global variable `x` is accessed and the value 1 is printed.

#### How does Python scope differ from other programming languages?

Python's scope differs from other programming languages in a few key ways:

* In many programming languages, variables defined within a block (such as a for loop or if statement) are not accessible outside of that block. However, in Python, variables defined within a block are accessible within the entire function or class.
* Some programming languages have a "block scope" where variables defined within a block are not accessible outside of that block, while others have a "function scope" where variables defined within a function are not accessible outside of that function. Python, however, has a "function scope" for local variables, but also allows for variables to be accessed within the enclosing scope.
* Some programming languages, such as C and C++, have a concept of pointers and references, which allows for variables to be passed by reference rather than by value. In Python, all variables are passed by reference, meaning that a change to a variable within a function will affect the original variable.

#### What to look out for when working with scope in Python

When working with scope in Python, there are a few things to look out for:

* Mutable default arguments: If a mutable object (such as a list or dictionary) is used as a default argument in a function, it can lead to unexpected behaviour. For example, consider the following code

```python
def my_function(x=[]):
    x.append(1)
    print(x)

my_function()  # prints [1]
my_function()  # prints [1, 1]
```

In the above example, the default value of the `x` argument is an empty list. However, since lists are mutable objects, any changes made to the list within the function will affect the original list. This can lead to unexpected behaviour, such as the output of the second call to `my_function` being `[1, 1]` instead of `[1]`. To avoid this, it is best practice to use immutable objects (such as None or integers) as default arguments, or to set the default value within the function.

* Global variables: Be careful when using global variables, as they can lead to unexpected behaviour if they are modified within a function or class. For example, consider the following code

```python
px = 1  # global scope

def my_function():
    global x
    x += 1
    print(x)

my_function()  # prints 2
print(x)  # prints 2
```

In the above code, we have a global variable `x` with a value of 1. Within the `my_function` function, the `global x` statement is used to indicate that the variable `x` is a global variable and should be modified. This leads to the value of `x` being incremented by 1 both within the function and outside of the function.

* UnboundLocalError: When you reassign a variable within a function that has the same name as a variable in the global scope, python will treat it as a local variable. This can lead to an UnboundLocalError when trying to access the variable before it has been assigned a value. To avoid this, you can use the `global` keyword to indicate that you want to reference the global variable, or you can use a different variable name.
* Be aware of the LEGB rule: Be aware of the LEGB rule to understand how python is resolving variable and function names.

#### Conclusion

Scope is an important concept in programming, and understanding how it works in Python can help you write more efficient and maintainable code. By being aware of the LEGB rule, mutable default arguments, global variables, and UnboundLocalError, you can avoid common pitfalls and write better Python code.
