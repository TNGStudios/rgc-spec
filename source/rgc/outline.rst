RGC: Main
==================================

This defines the entire JSON body inside RGC.

.. warning::
    Unless otherwise specified, fields are NOT nullable, and must be defined.

.. list-table:: Body
    :widths: 25 25 50
    :header-rows: 1

    *   - Key
        - Type
        - Description
    *   - ``rgcMeta``
        - :ref:`rgc_rgcmeta`
        - Contains information about the RGC file, including the format.
    *   - ``meta``
        - ``rgcMeta.format`` extended :ref:`rgc_meta`
        - Meta information about the song and chart.
    *   - ``events``
        - ``rgcMeta.format`` extended :ref:`rgc_events`
        - A dictionary containing arrays of all events in the chart.
