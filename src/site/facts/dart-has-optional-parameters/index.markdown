---
layout: fact
title: Dart has optional parameters
---
# {{ page.title }}

Functions and methods can declare optional parameters, which can have default
values and can be omitted by the caller.
Dart supports two types of optional parameters: _named_ and _positional_.

Named optional parameters must be called with their names
(consider the name part of the API). Positional
optional parameters are not called with names.

If an optional parameter is not given a default value, its default value is
`null`. You can detect if an optional parameter was provided with
`?parameter-name`, which returns true even if the parameter was called with
`null`.

Use optional parameters with default values when there is a common or
obvious value
for a parameter. Use named optional parameters when a name makes
the code clearer. For example, use named optional parameters with boolean
parameters.

## Example

Here is an example of a positional optional parameter with a default value.
The `port` parameter is optional because it is wrapped in square brackets `[ ]`.
If `post` is not provided by the caller, it has the default value `80`.

{% highlight dart %}
connectToWebServer(String hostName, String path, [int port=80]) {
  // ...
}

main() {
  connectToWebServer("example.com", "/index.html"); // port is 80
  connectToWebServer("example.com", "/index.html", 8080);  // port is 8080
}
{% endhighlight %}

Here is an example of named optional parameters with default values.

{% highlight dart %}
initializeValve(int valveNum, {bool flush: false, bool clean: false}) {
  // ...
}

main() {
  initializeValve(42);
  initializeValve(12, flush: true);
  initializeValve(13, clean: true);
  initializeValve(13, clean: true, flush: true);
}
{% endhighlight %}

Here is an example of detecting if an optional parameter was provided.

{% highlight dart %}
initializeValve(int valveNum, {bool flush: false, bool clean: false}) {
  if (?clean) {
    print("Clean was provided with a value of $clean.");
  } else {
    print("Clean was not provided.");
  }
}

main() {
  initializeValve(42);
  // Clean was not provided.
  
  initializeValve(88, clean: null);
  // Clean was provided with a value of null.
  
  initializeValve(13, clean: true);
  // Clean was provided with a value of true.
}
{% endhighlight %}