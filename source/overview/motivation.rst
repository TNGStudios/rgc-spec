Motivation: Why RGC?
==================================

####################################
Why make a rhythm game chart format?
####################################

The primary motivation for RGC is that existing rhythm game formats are difficult to parse.

Almost every rhythm game has invented their own way of storing chart information. Furthermore, there are often not specifications for how these files should be formated,
or what even constitutes a well-formed chart under some specifications.

What results from this is that, if someone wants to interact with format ``.xyz``, they would have to write their own parser, their own serialiser, and their own tools to work with it.

If they ever want to migrate to a different language, they have to write these tools again, if the format for ``.xyz`` changes underfoot as time goes on, they're screwed.

####################################
So what makes RGC easy to parse?
####################################

It's JSON. Almost every 'serious' programming language has JSON support either built in or with libraries. This means that parsing RGC in any language is as simple as parsing JSON, which is pretty simple.

Similarly, other design decisions have been made to make RGC as simple to work with as possible. For example, events are defined at a given ``ms``, instead of using ticks, measures or the alignment of the sun.

**RGC itself, is just a JSON schema.**

########################################################################
But you're proposing another format? Doesn't that add to the mess?
########################################################################

.. image:: ../_static/standards.png
  :width: 400
  :alt: XKCD: Standards

Under normal circumstances, I'd agree that this would contribute to a mess of more and more formats, except, there aren't actually existing standards for a rhythm game chart.

While there *are* lots of existing formats for rhythm game charts for **specific games**, there isn't actually a game-agnostic one.

Infact, RGC could be more suitably described as an interchange format for existing chart formats.

