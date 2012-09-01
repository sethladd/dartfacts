---
layout: fact
title: Dart is full of objects
---
# {{ page.title }}

Dart is an object-oriented language, and everything in Dart is an object. Even
functions and numbers are true objects. Dart does not have primitives, nor does
it have value types.

Unless initialized with a value, Dart objects are initialized to `null`.

The root class for all objects is Object.

## Example

{% highlight dart %}
class Point {
  final num x, y;
  Point(this.x, this.y);
}

main() {
  var age;
  assert(age == null);
  assert(age is Object);

  var p = new Point();
  assert(p is Object);
}
{% endhighlight %}