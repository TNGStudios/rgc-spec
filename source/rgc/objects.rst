.. _rgc_objects:

RGC: Objects
==================================

By default, this is empty (``{}``). Formats will extend this with object types.

That said, Formats are **NOT** free to extend this however they want. The expected format for extending this is defined below, where ``[objectType]`` is a generic objectType name.

.. list-table:: Body
    :widths: 25 25 50
    :header-rows: 1

    *   - Key
        - Type
        - Description
    *   - ``[objectType]``
        - List<``format [objectType]`` extends :ref:`rgc_object`>
        - Contains information about the RGC file, including the format.

As an example of this extension, lets say we have a format ``zkldi/some-rhythm-game``. This format defines the objectTypes NOTE and BPM.

The ``objects`` property inside the RGC **MUST** then be formatted like:

.. code-block:: JSON

   {
       "NOTE": [],
       "BPM": []
   }

Lets say our ``NOTE`` object defines a property of ``column``, we could then store an object like this:

.. code-block:: JSON

   {
       "NOTE": [{
           "ms": 100,
           "column": 1
       }],
       "BPM": []
   }

Since all objects **MUST** extend :ref:`rgc_object`, we also have to define an `ms` property.