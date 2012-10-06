---
layout: fact
title: Dart has rich collections
---
# {{ page.title }}

Dart's core libraries include a rich collection API. You can use
ordered lists, key/value maps, and sets of unique items. Methods are
provided for sorting items, finding items, transforming items, and more.

A _list_ is an ordered collection of items. You can access an item in a list
by its _index_.

A _map_ is a unordered collection key/value pairs. You can access a value in
a map by its _key_.

A _set_ is an unordered collection of unique items. Attempts to add duplicate
items are ignored.

## Example

Here is an example of using a list.

{% highlight dart %}
main() {
  var fruits = ['apples', 'bananas', 'oranges'];
  assert(fruits.length == 3);
  assert(fruits[1] == 'bananas');
  
  fruits.add("mangos");
  assert(fruits.length == 4);
  
  for (final fruit in fruits) {
    print(fruit);
  }
  
  var hasOranges = fruits.some((fruit) => fruit == 'oranges');
  assert(hasOranges);
  
  fruits.map((fruit) {
    return fruit.toUpperCase();
  }).forEach((f) {
    print(f);
  });
  
  // Or...
  
  fruits.map((fruit) => fruit.toUpperCase()).forEach((f) => print(f));
  
  fruits.clear();
  assert(fruits.length == 0);
}
{% endhighlight %}