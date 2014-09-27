### 1.2 Open Classes

- Gets a list of all methods in Ruby’s standard Array that begin with `re`

  ```
  [].methods.grep /^re/
  ```

- If you casually add bits and pieces of functionality to classes, you can end up with bugs like the one you just encountered

### 1.3 The Truth About Classes

- Even when you think you’re in control, you should still Monkey-patch with care

- Instance variables live in objects, and methods live in classes

- An object's instance variables live in the object itself, and an object's methods live in the object's class (That's why objects of the same class share methods but don't share instance variables)

- Classes *themselves* are nothing but objects

- Inherit: Class -> Module -> Object -> BasicObject

- A class is just a souped-up module with three additional methods— new(), allocate(), and superclass()

  ```
  inherited = falseClass.instance_methods(inherited) # => [:superclass, :allocate, :new]
  ```

### Objects and Classes Wrap-Up

> What's an object?

It's just a bunch of instance variables, plus a link to a class.

> What's a class?

It's just an object(an instance of Class), plus a list of instance methods and a link to a superclass. `Class` is a subclass of `Module`, so a class is also a module.
