---
layout: fact
title: Dart has operator overloading
---
# {{ page.title }}

You can use the special operator methods in a class, and redefine how
`+`, `-`, and other operators behave.

## Example

The `Money` class has implemented the `+` operator to return a new instance
with the combined amounts.

{% highlight dart %}
class Money {
  final int amount;
  Money(this.amount);
  Money operator +(Money other) {
    return new Money(amount + other.amount);
  }
}

main() {
  var payCheck = new Money(1000);
  var bonus = new Money(100);
  var total = payCheck + bonus;

  assert(total.amount == 1100);
}
{% endhighlight %}