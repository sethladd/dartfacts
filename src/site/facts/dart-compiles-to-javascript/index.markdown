---
layout: fact
title: Dart compiles to JavaScript
see-also:
  - dart-achieves-concurrency-via-isolates
learn-more:
  - title: The dart2js compiler
    url: http://www.dartlang.org/dart2js/
---
# {{ page.title }}

One of Dart's core design tenets is "compiles to logical and performant
JavaScript". As the lingua franca of the web, JavaScript is an important
deployment target for Dart. Dart's goal is to run across all major modern
browsers that support ES5 and HTML5.

The dart2js compiler, the third generation compiler produced by the Dart
team, is itself written in Dart. This compiler produces significantly
smaller output than the first generation compiler. A technique called
"tree shaking" is used to analyze the source code and imported libraries,
and trim unused code from the output.

A minification step will be added for dart2js, to produce even smaller output.

## Example

The output JavaScript is evolving. Here is a sample, as of 2012-09-01.

{% highlight dart %}
main() {
  print("Hello, Dart!");
}
{% endhighlight %}

The resulting JavaScript, unminified:

{% highlight javascript %}
function Isolate() {}
init();

var $$ = {};
var $ = Isolate.$isolateProperties;
$.Primitives_printString = function(string) {
  if (typeof dartPrint == "function") {
    dartPrint(string);
    return;
  }
  if (typeof console == "object") {
    console.log(string);
    return;
  }
  if (typeof write == "function") {
    write(string);
    write("\n");
  }
};

$.print = function(obj) {
  $.Primitives_printString(obj);
};

$.main = function() {
  $.print('Hello, Dart!');
};

var $ = null;
Isolate = Isolate.$finishIsolateConstructor(Isolate);
var $ = new Isolate();
if (typeof document != 'undefined' && document.readyState != 'complete') {
  document.addEventListener('readystatechange', function () {
    if (document.readyState == 'complete') {
      $.main();
    }
  }, false);
} else {
  $.main();
}
function init() {
Isolate.$isolateProperties = {};
Isolate.$finishIsolateConstructor = function(oldIsolate) {
  var isolateProperties = oldIsolate.$isolateProperties;
  var isolatePrototype = oldIsolate.prototype;
  var str = "{\n";
  str += "var properties = Isolate.$isolateProperties;\n";
  for (var staticName in isolateProperties) {
    if (Object.prototype.hasOwnProperty.call(isolateProperties, staticName)) {
      str += "this." + staticName + "= properties." + staticName + ";\n";
    }
  }
  str += "}\n";
  var newIsolate = new Function(str);
  newIsolate.prototype = isolatePrototype;
  isolatePrototype.constructor = newIsolate;
  newIsolate.$isolateProperties = isolateProperties;
  return newIsolate;
};
}
{% endhighlight %}

All Dart code runs in an Isolate, which is why you see an Isolate in the
output code.