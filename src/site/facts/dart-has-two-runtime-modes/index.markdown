---
layout: fact
title: Dart has two runtime modes
see-also:
  - dart-is-optionally-typed
---
# {{ page.title }}

Dart programs run in one of two modes: _production mode_ and _checked mode_.

In production mode, type annotations are ignored. Production mode is currently
the fastest runtime mode. Use production mode for production deployments.

In checked mode, _dynamic type assertions_ are inserted into the program and
checked at runtime. If a type assertion fails, it throws an exception. Use
checked mode for development and testing.

## Example

Consider the following code, in which the function `displayWelcome` has a typed
parameter of Person. It is called with two different variables, a Person
and then an Address.

{% highlight dart %}
displayWelcome(Person to) {
  print("Welcome to $to");
}

main() {
  var alice = new Person("Alice");
  displayWelcome(alice);

  var home = new Address("123 Main St");
  displayWelcome(home);
}
{% endhighlight %}

In production mode, the type annotation in displayMethod's signature is ignored.
Because all `displayMethod` does is print a string, the code works just fine
with both a Person and an Address.

    # Running production mode
    $ dart display.dart 
    Welcome to Alice
    Welcome to 123 Main St

In checked mode, however, a dynamic type assertion is added to check variables
being passed into displayWelcome. The runtime type assertion will fail when an
Address is passed in.

    # Running in checked mode
    $ dart --checked display.dart 
    Welcome to Alice
    Unhandled exception:
    type 'Address' is not a subtype of type 'Person' of 'to'.
    #0      displayWelcome (file:///Users/sethladd/tmp/display.dart:11:23)
    #1      main (file:///Users/sethladd/tmp/display.dart:20:17)


## Enable checked mode

Turn on checked mode in the Dart VM:

    dart --checked app.dart

Turn on checked mode in the Dart Editor:

<img src="imgs/dart-editor-checked-mode.png" alt="Checked mode in Dart Editor">