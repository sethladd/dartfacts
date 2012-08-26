---
layout: default
title: Dart classes have single inheritance
see-also:
  - dart-objects-have-class
---
# {{ page.title }}

Dart is a single inheritance language. This means that
a class can _extend_, or _inherit_ from, at most one other class.
Inheritance is great for creating more specialized versions
of a class.

## Example

In the following example, `Cat` is a more specialized verion
of `Animal`. That is, the concept of an animal is more abstract
than the concept of a cat.

{% highlight dart %}
class Animal {
  num health = 100;
  eat(num food) {
    health += food;
  }
  makeNoise(); // abstract
}

class Cat extends Animal {
  makeNoise() {
    print("Meow!");
  }
}
{% endhighlight %}

The `Animal` class is the _super class_ of `Cat`, while the
`Cat` class is a sub-class of `Animal`.

There can be many classes in the hierarchy. For example:

{% highlight dart %}
class Animal {
  // ...
}

class Mammal extends Animal {
  // ...
}

class Feline extends Mammal {
  // ...
}

class DomesticatedCat extends Feline {
  // ...
}
{% endhighlight %}

Give the above example of `DomesticatedCat` extending
from `Feline`, and `Feline` extending from `Mammal`,
and `Mammal` extending from `Animal`, all the following
are true:

{% highlight dart %}
main() {
  var misterBigglesworth = new DomesticatedCat();
  assert(misterBigglesworth is DomesticatedCat);
  assert(misterBigglesworth is Feline);
  assert(misterBigglesworth is Mammal);
  assert(misterBigglesworth is Animal);
}

{% endhighlight %}

{% include see-also.html %}