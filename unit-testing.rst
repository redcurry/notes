Growing Object-Oriented Software, Guided by Tests
=================================================

*Notes from book by Freeman and Pryce.*

Chapter 1
---------

Start by writing an acceptance test, which tests a new, large feature.
In order to make the acceptance test pass, we must write (and pass) several unit tests.

Integration tests test the layer of abstraction over third-party APIs.

Chapter 2
---------

See book by Wirfs-Brock and McKean for object design.

Avoid navigating other objects to get what you want. For example::

    master.allowSavingOfCustomizations();

vs.::

    master.getModelisable()
        .getDockablePanel()
            .getCustomizer()
                .getSaveItem()
                    .setEnabled(false);

Chapter 4
---------

Start a project by writing the simplest possible application
that can be built, deployed (to a production-like environment),
and tested end-to-end (very important).

This first system should include its major components
and how they will communicate---draw on a board---
but it doesn't have to be perfect.

Release frequently (by automation) as changes are made
in order to obtain feedback from real users.

On an existing system, start by automating the build and deployment
processes. Then start testing the simplest path through the system,
and move on to the more complicated code.

Chapter 5
---------

Write the acceptance test using the language of the application's domain
(not technologies, like databases).

Separate unit & integration tests, which should pass on every build,
from acceptance tests, which should pass when a feature is completed.

Start testing the successful path, not cases that are supposed to fail,
but write down those cases while coding to test later.

Write a test clearly, as if the code to write it already exists,
then build the supporting code to make the test pass.

Don't starting writing a feature by writing (and unit-testing) the domain model;
start by going through the inputs (e.g., a mouse click) until they arrive
at the model, and then follow the path to the output.

Unit-test a feature's behavior, not every method and all paths of the code.
Testing a feature would test the collaborations between objects,
which helps us to understand the roles of those classes.

If writing the next test is difficult, it is a sign that the software design
needs to be improved, so refactor until the test becomes easy to write.

Can't test everything up-front, but it's important to think about
the testing strategy. For example, important logic may need be tested more,
unhandled exceptions may need more integration testing, and
system failures may need more thorough testing.

Chapter 6
---------

Separate groups of code by how much the groups may change for the same reasons
(i.e., code that changes for the same reasons belong together).

True encapsulation ensures that an object's behavior is only affected
by its API, not by other object dependencies.

Don't expose too much of an object's internals through its API
or objects that use it may end up doing some of its work.

One should be able to describe what an object does without using
"ands" or "ors." If so, break up the object.

When creating a new object, pass in all its dependencies through the
constructor, don't do it later with properties.

Notifications and adjustments don't have to be passed to the constructor,
as defaults may be created and then changed later.

The API of an object should not be more complicated than that
of its components.

Objects should be context-independent; that is, not know
about the system in which it executes, passing it the context
through a constructor or methods.

Chapter 7
---------

TDD helps with design by (1) describing the *what*, not the how,
(2) keeping objects small and focused (because tests should be short),
and (3) keeping objects independent (because we have to explicitly
send the dependencies by testing).

Communication patterns between objects are more important
than their internal structure.

"An interface describes whether two components will fit together,
while a protocol describes whether they will work together."
(Communication protocols are typically implicit because the language
does not support defining object relationships.)

Mock an object's peers---dependencies, notification, or adjustments---
not its internals. Such tests help decide whether they really are peers.

Define types for all domain concepts, even if they're value types,
like String (immutable). It makes finding them easier and allows for better
object-oriented design in case behavior needs to be added.

How to introduce a value type: break up complex code, introduce a
placeholder type that wraps a single field and add more fields or methods,
and group types that are used together so as to hide them behind an interface.

For objects, follow similar principles as above. Start by breaking up
an abojcet if it's too large to test easily. Unit-test those parts separately.

When we discover that an object requires a service, implement
its interface and mock it out in a unit test. Then implement the class
that provides the service and discover what services it needs, and so on.

Clusters of related objects that work together should be packaged
into a containing object---"composite simpler than the sum of its parts."

An interface and its single implementation shouldn't be named almost the same.
There must be something specific about the implementation
that can be included in the class name; otherwise, it may mean
that the interface is poorly named or designed---it may have too many responsibilities.

Classes are an implementation detail---a way to implement types,
not the types themselves, which are interfaces.

Chapter 8
---------

Don't mock third-party APIs. Instead, write an adapter layer based on
what our objects need and in our domain language. Test this layer
with integration tests to understand how the third-party library works.

Some third-party value types may be used directly, but often
we need to translate them to the application domain.

Part III
--------

Page 112 - "Start with the outside event that triggers the behavior
we want to implement and work out way into the code an object at a time,
until we reach a visible effect (such as a sent message or log entry)
indicating that we've achieved our goal."

Page 112 - We can't test all configuration options in an entire system,
but we can exercise it as much and as early as possible
