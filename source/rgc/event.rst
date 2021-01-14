.. _rgc_event:

RGC: Event
==================================

This is the expected base properties for any Event. That is to say, any ``format`` extending an event **MUST** have these properties defined properly.

.. note::

    For custom format creators: If your event does not need a milisecond timestamp, it is metadata.

.. list-table:: Body
    :widths: 25 25 50
    :header-rows: 1

    *   - Key
        - Type
        - Description
    *   - ``ms``
        - Positive Integer
        - The time in Miliseconds when this event occurs.