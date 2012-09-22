---
layout: fact
title: Dart is optionally typed
see-also:
  - dart-has-two-runtimes-modes
learn-more:
  - title: Optional Types in Dart
    url: http://www.dartlang.org/articles/XXXXX
---
# {{ page.title }}

Dart is an optionally typed language. The static type annotations do not
affect the runtime semantics of the code.

Treat static types as _annotations_, adding extra inline documentation
for your fellow developers. Tools like editors and analyzers can use the
static type annotations to provide more feedback and early warning detection.

Types are optional to help developers write programs quickly, without being
caught up in ceremonial type checkers. Add types when you are comfortable with
the design, or omit types when you need to express something that is otherwise
impossible to express with traditional type systems.

## Example

An untyped function:

{% highlight dart %}
adjustDingleArm(amount, depleneration, axis) {
  // proprietary function
}
{% endhighlight %}

In the above example, notice the `this.x` in the
constructor. This syntactic sugar eliminates the tedious
pattern `this.x = x` that most constructors share.