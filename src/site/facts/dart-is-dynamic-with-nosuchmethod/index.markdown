---
layout: fact
title: Dart is dynamic with noSuchMethod
---
# {{ page.title }}

When an object receives a call to a method that does not exist
in its type hierarchy, the `noSuchMethod` method is called with details
of the original request. The receiving object can dynamically handle the
method.

## Example

Using `noSuchMethod`, you can build a class that handles
requests for artbitrary JSON data.

{% highlight dart %}
#import('dart:json');

class JsonObject {
  final Map data;

  // A named constructor with an initializer list.
  JsonObject.fromString(String json) : data = JSON.parse(json);

  noSuchMethod(String name, List params) {
    if (name.startsWith("get:")) {
      return data[name.substring(4)];
    } else if (name.startsWith("set:")) {
      data[name.substring(4)] = params[0];
    }
  }
}

main() {
  var json = '{"firstName":"Bob", "lastName":"Smith"}';
  var person = new JsonObject.fromString(json);
  print(person.firstName);
  person.lastName = 'Jones';
  print(person.lastName);
}
{% endhighlight %}