---
layout: fact
title: Dart code is not compiled to bytecode
---
# {{ page.title }}

Unlike other VM based languages, the Dart VM does not load bytecode. The Dart VM
instead loads, parses, and compiles Dart source code. When the VM is asked to
run a Dart program, it first compiles the code into an internal representation,
and then into machine code.

By compiling the code, the VM spares developers of
potentially lengthy compilation steps.