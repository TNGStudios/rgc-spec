The Format Version Field
==================================

##################################
Formats and Time
##################################

It's no secret that games add features over time. The standard format library has to handle this one way or another, but we run into a pretty irritating issue.

To use a real world example, let's consider the changing of certain metadata properties from IIDX 26 ROOTAGE to IIDX 27 HEROIC VERSE.

In ROOTAGE, the difficulty names were NORMAL, HYPER and ANOTHER. In HEROIC VERSE, a fourth difficulty was added - LEGGENDARIA.

Now, nothing really significant has changed to the format here, but we would have to create a new format to indicate this is now a possible value.

But, that sucks; we'd have loads and loads of formats, and we'd have to backtrack among all IIDX games in order to create separate formats for each.

The work on serialisers would be immense, and they'd have to update/repeat a lot of code a lot of the time.

But, format versioning doesn't magically solve this problem. We'd just be shifting the problem form "loads of formats" to "loads of formatVersions".
The selling point of RGC - that it's easy to parse and work with - would be completely neutered if parsers and serialisers had to account for 15 different formats in different ways.

##################################
Watch For Rolling Supersets
##################################

Our solution is simpler, but does miss some of the finer details. ``formatVersion`` is a single positive integer, starting at 1. **Future changes are rolled into a superset of the previous format**.

In our previous example, that means that, if IIDX20 was ``formatVersion: 1``, IIDX21 would be ``formatVersion: 2``, and the format specification would allow ``difficulty`` to be anything it was before, and LEGGENDARIA.

Now, this makes the jobs of serialisers pretty easy. **All format versions are therefore future-compatible, so checking whether a serialiser can handle a file is a single statement.**

As an example, let's say we have a serialiser that supports IIDX20. Since all future versions are supersets, all we need to do is check:

``if (formatVersion >= 1)``

to know if our serialiser could assume the properties it needs to inside the RGC file.

In short, this ensures that:

- Existing scripts are never broken by future versions.
- There aren't a billion different formats for the same game flying around.
- Version checking is a one-statement operation, and removes a lot of the serialisers responsibility.

##################################
Issues with this approach
##################################

Redundant data, sometimes.

Let's consider a game changing the name of a difficulty.

The new ``difficulty`` metadata property for the game will have to then support either name for the difficulties, even if one of them only really makes sense.

Code interacting with RGC is free to have its own opinion on how it handles the redundant information.

##################################
When does it become a new format?
##################################

Either:

If the changes are "significant", such as the change between Reflec Beat's VOLZZA 2 and Reflesia, where an entire type of note was removed, and replaced with another.

.. note::
    Yes, technically you could roll this into a superset by defining a new object type, and expecting people to ignore the old one.
    However, *technically*, you could also roll every single game into one superset, and expect people to ignore the fields they don't need.

Or if the changes are not able to be places into one superset, such as if a game has a property that, in the future, made existing values invalid.

As an example, if a game went from having 6 columns, and a ``NOTE.col`` property that went from 0-5, then the game changes to only having 4 columns.

Existing code could no longer safely make assumptions about the values inside future versions, and therefore a new format would be needed.

This example is a little contrived, as we have tried to design this such that these events are rare, or clearly distinguished by the release of a new game (see reflec, above).