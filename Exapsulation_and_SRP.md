# Encapsulation

Encapsulation is an Object Oriented Programming concept that binds together the data and functions that manipulate the data, and that keeps both safe from outside interference and misuse.

It is used as a mechanism to restrict direct access to objects’ data and methods. But the same time it facilitates operation on that data (objects’ methods).

Encapsulation tells us that we should know just an interface of class to be able to use it. We don't have to know anything about internals of class to be able to use it.

# Cohesion & Coupling

Cohesion is about the relationship between all the methods inside a class. Are they using the same set of instance variables & parameters, all working together towards the same goal? Or does every method feel separate from each other?
```
class Library
  def lend_book
  end

  def return_book
  end

  def make_coffee
  end
end
```
In this example make_coffee stands out quite a bit, even if this library has a cafeteria it makes no sense for the Library class to be making coffee 

Coupling is how dependent is a class to other classes, how “tied together” is it to the rest of the system, and the ability of this class to be used in isolation.

```
class ShoppingCart
  attr_accessor :items

  def initialize
    @items = []
  end
end

class Order
  def process_order(cart)
    cart.items.map(&:price).inject(:+)
  end
end
```
In this example Order is highly coupled to ShoppingCart because it knows too much about it, it knows there is an items variable & it’s doing some calculation with that.

Now if you change ShoppingCart‘s implementation of items, you’ll also have to change Order.
class ShoppingCart
```
  attr_accessor :items

  def initialize
    @items = []
  end

  def calculate_total
    items.map(&:price).inject(:+)
  end
end

class Order
  def process_order(cart)
    cart.calculate_total
  end
end
```
We have reduced coupling by moving the details of the calculation where they belong.