Growing Object-Oriented Software, Guided by Tests
=================================================

*Notes from book by Freeman and Pryce.*

Start by writing an acceptance test, which tests a new, large feature.
In order to make the acceptance test pass, we must write (and pass) several unit tests.

Integration tests test the layer of abstraction over third-party APIs.

See book by Wirfs-Brock and McKean for object design.

Avoid navigating other objects to get what you want. For example::

    master.allowSavingOfCustomizations();

vs.::

    master.getModelisable()
        .getDockablePanel()
            .getCustomizer()
                .getSaveItem()
                    .setEnabled(false);
