[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# Object Composition and Mixins in Ruby

## Prerequisites

-   [ga-wdi-boston/ruby-vs-js-objects](https://github.com/ga-wdi-boston/ruby-vs-js-objects)
-   [ga-wdi-boston/ruby-vs-js-objects-inheritance](https://github.com/ga-wdi-boston/ruby-vs-js-objects-inheritance)

## Objectives

By the end of this, students should be able to:

-   Give two reasons why composition and Mixins are desirable.
-   Write a class which inherits from another class.
-   Describe why composition is preferred to inheritance.

## Preparation

1.  [Fork and clone](https://github.com/ga-wdi-boston/meta/wiki/ForkAndClone)
    this repository.
1.  Install dependencies with `bundle install`.

## JavaScript Inheritance

## There is a Better Way (Composition)

Classical inheriterance has its limitations and we don't want to limit
ourselves, that's where composition comes in.  Let's discuss the code below:

```ruby
class Car
  attr_reader :engine
  def initialize
    @engine = 1200
  end
end

class Ford < Car
end

car = Ford.new
puts car.engine
```

Whenever I create a new instance of a `Ford`, on initialization an instance of
a `Car` is created as well. This instance of car has all of the methods defined
in the `Car` class. *It inherits all of methods defined in the `Car` class.*

## An Even Better Way (Mixins)

We want to make chunks of code that are resuable across of multiple classes.
These "chunks" are called `modules`. Take a look at the code below:

```ruby
module Sleeper
  def go_to_sleep
    # code here
  end
end

class Person
  include Sleeper
end

class Computer
  include Sleeper
end
```

In the code above we defined a `module` called Sleeper. We also define a
`Person` class and a `Computer` class. By using the keyword `include` followed
by the name of the module (in this case `Sleeper`) we have access to the methods
we defined in our module.  This is great because it allows us to keep our code
*D-R-Y*, not to mention it allows us to be lazy developers (the good kind of
lazy).

## Lab: Model Shapes Using Classes

In a [previous
lab](https://github.com/ga-wdi-boston/ruby-vs-js-objects#lab-creating-a-shape-class),
you were asked to create and use a `Shape` class.

A `Rectangle` is a `Shape`, and a `Square` is a `Rectangle`.

Create a `Rectangle` that inherits from `Shape`. You will need to override the
constructor method inside `Rectangle` to take two sides of different lengths.
Since all rectangles have four sides, you can set a default value for `@sides`
inside `Rectangle`'s constructor.

Requirements for `Rectangle`s:

-   Rectangles should be instantiated with `Rectangle.new(3, 4)` to create a
    rectangle with a length of 3 and a width of 4.
-   Instances of Rectangle should respond to the `#area` method and give the
    correct result.
-   Do not override anything that doesn't need to be overriden.

Next, create a `Square` class that inherits from `Rectangle`.

Requirements for `Square`s:

-   Squares should be instantiated with `Square.new(4)` to create a square with
    all sides equal to 4.
-   Instances of Square should respond to the `#area` method and give the
    correct result.
-   Do not override anything that doesn't need to be overriden.

## Additional Resources

-   [Useful links to documentation](https://www.ruby-lang.org/en/documentation/)
-   [Stack Overflow: Inheriterance](http://stackoverflow.com/questions/15754768/when-do-we-use-ruby-module-vs-using-class-composition)

## [License](LICENSE)

1.  All content is licensed under a CC­BY­NC­SA 4.0 license.
1.  All software code is licensed under GNU GPLv3. For commercial use or
    alternative licensing, please contact legal@ga.co.
