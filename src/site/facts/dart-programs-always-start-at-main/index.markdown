---
layout: fact
title: Dart programs always start with main
---
# {{ page.title }}

Dart programs are structured, and begin their execution in the `main()`
function. The parsing, compiling, and initializing steps do not execute
Dart code. You can be sure that code does not execute until `main()` is run.

## Example

{% highlight dart %}
dealCards() {
  // ....
}

setUpBoard() {
  // ....
}

play() {
  // ....
}

// Program starts here.
main() {
  dealCards();
  setUpBoard();
  play();
}
{% endhighlight %}