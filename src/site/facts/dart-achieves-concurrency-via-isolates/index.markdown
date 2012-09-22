---
layout: fact
title: Dart achieves concurrency via Isolates
learn-more:
  - title: Isolates in Dart Library Tour
    url: http://www.dartlang.org/library-tour/#dartisolate---concurrency-with-isolates
---
# {{ page.title }}

Dart allows you to unlock the performance of modern multi-core machines with
Isolates, an abstraction for concurrency and partitioning in Dart.

All Dart code runs inside an isolate. Isolates can run in separate threads or
processes, or even in Web workers for HTML5 apps.

Isolates do not share memory or state, thus
reducing common bugs with traditional shared-state multi-threaded concurrency.
Isolates communicate via message passing over ports. Messages are
copied before received, thus ensuring no state is shared.

# Example

In the below example, there are two isolates running: the `main()` program,
and the `echo()` function. A message ("Hello from main") is sent to the
echo isolate via its SendPort. The reply is sent over a different port.

{% highlight dart %}
#import('dart:isolate');

// This is spawned into an isolate.
echo() {
  port.receive((msg, reply) {
    reply.send("I received: $msg");
  });
}

// This runs in an isolate.
main() {
  SendPort sendPort = spawnFunction(echo);
  sendPort.call("Hello from main").then((reply) {
    print(reply);    // I received: Hello from main
  });
}
{% endhighlight %}