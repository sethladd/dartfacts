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
state (variables and their values) and behavior (methods)
are defined by its class (and its class's
parent class, up to the Object class).

## Example

A Dart class looks familiar, but has a few enhancements.
Can you spot one below?

{% highlight dart %}
#import('dart:math');

class Point {
  num x, y;
  Point(this.x, this.y);
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