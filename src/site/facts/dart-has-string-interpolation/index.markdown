---
layout: fact
title: Dart has string interpolation
---
# {{ page.title }}

You can construct a string in Dart with string interpolation. Insert a variable
with `$name`, or insert the result of an expression with `${expression}`.

## Example

{% highlight dart %}
main() {
  var emotion = 'happy';
  var message = 'I am feeling $emotion.';
  var extremeMessage = 'I am feeling ${emotion.toUpperCase()}!!!';

  assert(message == 'I am feeling happy.');
  assert(extremeMessage == 'I am feeling HAPPY!!!');
}
{% endhighlight %}
