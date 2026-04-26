# LuaPyOOP

Adds Python-style classes to Lua!

Simply import this module using the `require` function and create Python-style classes:

```
local class = require '.lib.class'

local MyClass = class.classify("MyClass", {})

function MyClass:my_method()
    print("Called from "..tostring(self))
end

local MySubClass = class.classify("MySubClass", {}, {MyClass})

local my_instance = MySubClass()
```

This gives you advanced inheritance, but also a few of Python's built-in functions (`dir`, `isinstance`, `issubclass`) and classes (`Type`, `Object`), and method binding to create your classes in Lua with the same style as Python's Object-Oriented Programming.

```
>>> my_instance
<MySubClass object at 0x........>
>>> my_instance.my_method
<bound method 'my_method' of instance of class 'MySubClass'>
>>> my_instance.my_method()     -- The 'self' argument has been bound to my_instance
Called from <MySubClass object at 0x........>
>>> MySubClass.my_method()      -- Not bound to any instance.
Called from nil
>>> class.Type(my_instance)
<Class 'MySubClass'>
>>> class.Type(MyClass)
<Class 'Type'>
```