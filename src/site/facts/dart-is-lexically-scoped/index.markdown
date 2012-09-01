---
layout: fact
title: Dart is lexically scoped
see-also:
  - dart-has-string-interpolation
---
# {{ page.title }}

The Dart language is lexically scoped. This means that the scope of names is
defined by where they occur in the source code. Lexical scope is statically
defined by the code, and thus easy to reason about and visually confirm.

Among other things, this means that closures are lexically scoped, behaving
in a more logical manner.

## Example

In the example below, a click handler is added in the constructor of
`FeedButton`. The handler calls `this.feedLlamas()`, and because of
lexical scope, `this` is the FeedButton instance.

{% highlight dart %}
#import('dart:html');

class FeedButton {
  final ButtonElement button;
  final List<Llama> llamas;

  FeedButton(String buttonId, this.llamas) : button = query('#$buttonId') {
    button.on.click.add((e) => this.feedLlamas());
  }

  feedLlamas() {
    llamas.forEach((llama) => llama.feed());
  }
}
{% endhighlight %}
