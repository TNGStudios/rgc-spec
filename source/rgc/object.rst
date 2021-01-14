.. _rgc_object:

RGC: Object
==================================

This is the expected base properties for any Object. That is to say, any ``format`` extending an object **MUST** have these properties defined properly.

.. note::

    For custom format creators: If your object does not need a milisecond timestamp, it is metadata.

.. list-table:: Body
    :widths: 25 25 50
    :header-rows: 1

    *   - Key
        - Type
        - Description
    *   - ``ms``
        - Positive Integer
        - The time in Miliseconds when this object occurs.