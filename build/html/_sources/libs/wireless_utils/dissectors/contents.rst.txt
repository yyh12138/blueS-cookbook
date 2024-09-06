dissectors
=============

.. py:class:: Dissector 

    This class is a dissector class that can convert a complex data to raw bytes, or raw bytes to a complex data.
    Every dissector class must inherit this class, like UUID dissector, flag dissector, etc

    Two methods must be implemented in the inherited class: :py:meth:`build` and :py:meth:`dissect`

    .. py:method:: __init__(data=b"", length=-1, content={}, *args, **kwargs)

        This method initializes the dissector

        :param bytes data: the data to convert
        :param int length: the length of the data
        :param dict content: the content of the data

    .. py:method:: build()

        This method converts the special content to raw bytes.
        It must be implemented in the child class


    .. py:method:: dissect()

        This method converts the raw bytes to speical content.
        It must be implemented in the child class

    