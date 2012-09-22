---
layout: fact
title: Dart has a package manager
learn-more:
  - title: Pub, the Dart package manager
    url: http://www.dartlang.org/pub-package-manager/
---
# {{ page.title }}

Dart bundles a package manager, affectionately called _pub_, with the Dart SDK.
You can use pub to install and upgrade _packages_, which contain Dart libraries
and code.

Soon, you'll be able to search for and discover packages, as well as publish
your own packages.

## Example

To use pub, first create a `pubspec.yaml` file for your application. Declare
the name of your application, and any dependencies.

{% highlight yaml %}
name: my-app
dependencies:
  unittest:
    sdk: unittest
  example-mock:
    git: git://example.com/example-mock.git
{% endhighlight %}

Notice how there are
currently two ways to get packages: from the Dart SDK or from git.

Next, install the packages for your application.

{% highlight bash %}
> cd my-app
> export DART_SDK=/path/to/dart/sdk
> export PATH=$PATH:$DART_SDK/bin
> pub install
{% endhighlight %}

You can now use the unittest and example-mock in your application, by importing
the libraries with the `package:` prefix

{% highlight dart %}
#import('package:unittest/unittest.dart');
#import('package:example-mock/example-mock.dart');

main() {
  // ...
}
{% endhighlight %}