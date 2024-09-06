packets
========

.. py:class:: Packet

    This class represents an abstract of a packet.
    It can be overloaded to implement specific packet types

    .. py:method:: __init__(self, packet=None, additionalInformations=None)

        :param bytes packet: The raw packet
        :param dict additionalInformations: Additional informations about the packet

    

    .. py:method:: toString()

        This method converts the packet to a string, like ``<< name >>``

    .. py:method:: __str__()

        This method converts the packet to a string, like ``<< [additionalInformations] name >>``

.. py:class:: WaitPacket(Packet)

    This class represents a given special packet that is used to wait for a given time

    .. py:method:: __init__(time=0.0)

        :param float time: The time to wait
    
    .. py:method:: toString()

        This method converts the packet to a string, like ``<< name | time >>``
    