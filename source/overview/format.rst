The Format Field
==================================

##################################
Game-specific implementations
##################################

You might be confused as to how one single format can possibly anticipate everything a rhythm game could throw at it.

Simple: It doesn't try to.

RGC works as a skeleton schema. It requires certain properties to be defined, then uses a parameter to define a ``format``.

This ``format`` defines an extension to the spec, for what that specific game may want.

With this, we can enforce sensible properties for games, while giving the format free reign to extend where necessary.

##################################
Avoiding Fragmentation
##################################

This is cool and all, but surely this suffers the standard fragmentation mentioned before? What if two people define different formats for one game?
Do I have to make my own format?

This has also been thought through. The ``format`` string property in RGC **MUST** follow a ``namespace/name`` format.

As an example, if I wanted to define my own schema for CHUNITHM, I would use the format name ``zkldi/chunithm``, or similar.

The point of the namespacing is to vastly reduce chances of collision between users.

And as for avoiding initial fragmentation, the RGC spec also defines a standard library of formats for popular games. These are prefixed with the ``std/`` namespace.

The RGC spec reserves the ability to define anything under the ``std/`` namespace, and as such, you **MUST** not implement custom formats inside of it.

As an example, if I wanted to parse Single Player IIDX, I would use the ``std/iidx-SP`` format.

.. note::

    There are other restrictions on what characters can go inside the ``format`` field. These restrictions can be found at :ref:`rgc_rgcmeta`

##################################
Why custom formats?
##################################

There are a lot of rhythm games, and it is a lot of work to define a schema for every single one. With dedicated custom format support, people are free to define that part themselves.

Those games may become a part of the standard in the future, and because of the namespacing, that would not break existing custom formats for that game.

##################################
What can a format extend?
##################################

A format is free to add any field inside ``meta``, and is free to define new Object Types inside ``objects``. More information about this can be found at :ref:`rgc_objects`.