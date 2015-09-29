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
