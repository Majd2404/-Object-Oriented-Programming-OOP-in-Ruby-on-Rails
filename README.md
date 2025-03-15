# Object-Oriented Programming (OOP) in Ruby on Rails

## Introduction
Object-Oriented Programming (OOP) is a programming paradigm based on objects that encapsulate data and behavior. Ruby on Rails, being a framework built on Ruby (a pure object-oriented language), heavily relies on OOP principles.

This tutorial covers the four key principles of OOP in the context of Ruby on Rails:
- **Encapsulation**
- **Abstraction**
- **Inheritance**
- **Polymorphism**

## 1. Encapsulation
Encapsulation is the practice of bundling data and methods that operate on that data into a single unit (class). It helps protect the data from unintended modifications.

### Example:
```ruby
class User
  attr_accessor :name, :email

  def initialize(name, email)
    @name = name
    @email = email
  end

  def display_info
    "User: #{@name}, Email: #{@email}"
  end
end

user = User.new("Majd", "majd@example.com")
puts user.display_info
```

## 2. Abstraction
Abstraction hides implementation details and exposes only necessary functionality to the user.

### Example:
```ruby
class Payment
  def process_payment(amount)
    raise NotImplementedError, "This method should be overridden in a subclass"
  end
end

class CreditCardPayment < Payment
  def process_payment(amount)
    "Processing credit card payment of $#{amount}"
  end
end

payment = CreditCardPayment.new
puts payment.process_payment(100)
```

## 3. Inheritance
Inheritance allows a class to inherit behavior and properties from another class.

### Example:
```ruby
class ApplicationRecord < ActiveRecord::Base
  self.abstract_class = true
end

class User < ApplicationRecord
  validates :name, presence: true
end
```
Here, `User` inherits from `ApplicationRecord`, which in turn inherits from `ActiveRecord::Base`.

## 4. Polymorphism
Polymorphism allows different classes to respond to the same method call in different ways.

### Example (Single Table Inheritance - STI):
```ruby
class Payment < ApplicationRecord
end

class CreditCardPayment < Payment
end

class PayPalPayment < Payment
end
```
Now, we can call `Payment.all` and get all types of payments, whether `CreditCardPayment` or `PayPalPayment`.

## Conclusion
OOP principles help keep Rails applications organized, scalable, and maintainable. Using encapsulation, abstraction, inheritance, and polymorphism, you can build robust Rails applications with reusable and modular code.

---
Happy Coding! 🚀
