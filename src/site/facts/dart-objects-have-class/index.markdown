---
layout: fact
title: Dart objects have class
see-also:
  - dart-classes-have-single-inheritance
learn-more:
  - title: Classes from Dart Language Tour
    url: http://www.dartlang.org/language-tour/#classes
---
# {{ page.title }}

Dart is a class-based object oriented language. An object's
_state_ (variables and their values) and _behavior_ (methods)
are defined by its class (and its class's
parent class, up to the root Object class).

## Example

A Dart class looks familiar, but has a few enhancements.
Can you spot one below?

{% highlight dart %}
#import('dart:math');

class Point {
  // The state of the object is defined by fields.
  num x, y;
  
  // The constructor creates a new instance of a class.
  Point(this.x, this.y);

  // The behavior of the object is defined by methods.
  num distanceTo(Point other) {
    var dx = x - other.x;
    var dy = y - other.y;
    return sqrt(dx * dx + dy * dy);
  }
}
{% endhighlight %}

In the above example, notice the `this.x` in the
constructor. This syntactic sugar eliminates the tedious
pattern `this.x = x` that most constructors share.