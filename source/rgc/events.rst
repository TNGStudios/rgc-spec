.. _rgc_events:

RGC: Events
==================================

By default, this is empty (``{}``). A ``format`` will extend this with event types.

That said, A ``format`` is **NOT** free to extend this however it wants. The expected format for extending this is defined below, where ``[eventType]`` is a generic eventType name.

.. list-table:: Body
    :widths: 25 25 50
    :header-rows: 1

    *   - Key
        - Type
        - Description
    *   - ``[eventType]``
        - List<``format [eventType]`` extends :ref:`rgc_event`>
        - Contains information about the RGC file, including the format.

As an example of this extension, let's say we have a format ``zkldi/some-rhythm-game``. This format defines the eventTypes NOTE and BPM.

The ``events`` property inside the RGC **MUST** then be formatted like:

.. code-block:: JSON

   {
       "NOTE": [],
       "BPM": []
   }

Let's say our ``NOTE`` event defines a property of ``column``, we could then store an event like this:

.. code-block:: JSON

   {
       "NOTE": [{
           "ms": 100,
           "column": 1
       }],
       "BPM": []
   }

Since all events **MUST** extend :ref:`rgc_event`, we also have to define an `ms` property.