better-java8-monads
==================

I can't help but feel there were some important omissions in the Java8 library.
Stream and Optional are great, but we need to get unimplicit effects like Exceptions out of the code too.
To make a much more readable code base, I'll try to supply some monads to fill in the gaps.

Usage
=====

Import into your project:

SBT
---

    "com.jason-goodwin" % "better-monads_2.10" % "0.0.1"

Maven
-----

    <dependency>
	    <groupId>com.jason-goodwin</groupId>
	    <artifactId>better-monads_2.10</artifactId>
	    <version>0.0.1</version>
    </dependency>

Note on Published Artifact
--------------------------

Currently published version had problems with javadoc so the project was published as a scala project.
It currently has a scala version ammendment in the name (_2.10). This will be fixed in future versions.

Try
===

The try monad was attributed to Twitter and placed into the Scala standard library.
While both Scala and Haskell have a monad Either which has a left and a right type, 
a Try is specifically of a type T on success or an exception on failure.

Usage
-----

The Try api is meant to be similar to the Optional type so has the same functions.
- map(x) maps the success value x to a new value and type or otherwise passes the Failure forward.
- flatMap((x) -> f(x)) maps the success value x to a new Try of f(x).
- recover((t) -> x) will return the success value of the Try in the success case or the value x in the failure case. Exposes the exception.
- recoverWith((t) -> f(x)) will return the success value of the Try in the success case or a new try of f(x) in the failure case. Exposes the exception.
- orElse(x) will return the success value of the Try in success case or the value x in failure case.
- orElseTry(f) will return the success value of the Try in success case or a new Try(f) in the failure case.

See the tests for examples of all functionality.
