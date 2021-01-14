What is a chart?
==================================

It's important, before showing RGC, to understand what we define a chart as.

#################
Defining Objects
#################

RGC interprets a chart as being made of two parts, Objects and Metadata.

An object, in RGC, is simply any event that happens at a certain time. Notes, for example, would be an object.

Similarly, non-playable events are also objects, such as BPM changes or measure changes.

In short, anything that happens at a given time is an object to RGC.

To store objects in RGC, RGC uses an Object Type. For example, Notes in ``std/iidx-SP`` have the type of ``NOTE``, BPM objects have the type of ``BPM`` and so on.

#################
Defining Metadata
#################

Metadata, on the other hand, is anything that the chart has stored that **does not** happen at a given time.

For example, the title, artist and charter of the song are all metadata, as they are timestamp agnostic.

In short, anything that is stored about the chart that does not happen at a given time, is metadata.