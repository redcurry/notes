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
