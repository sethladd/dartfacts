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

Optional types help developers write programs quickly, without being
caught up in ceremonial type checkers. Add types when you are comfortable with
the design, or omit types when you need to express something that is otherwise
impossible to express with traditional type systems.

## Example

Start by exploring the program design:

{% highlight dart %}
// warrior is type dynamic.
equipForBattle(warrior) {
  var weapon = new Sword();
  warrior.equip(weapon);
}
{% endhighlight %}

Later, as you become more comfortable with the design,
add type annotations to the public API:

{% highlight dart %}
// warrior is now a Warrior.
equipForBattle(Warrior warrior) {
  var weapon = new Sword();
  warrior.equip(weapon);
}
{% endhighlight %}

Notice how `weapon` is typed with `var`, which is a shorthand for `dynamic`.
It is common to leave variables as dynamic inside methods or functions. Tools
can perform local type inferencing.