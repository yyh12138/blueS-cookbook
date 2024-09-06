callback
===========

.. py:class:: Callback 

    This class is a callback class that can be linked to an event

    .. py:method:: __init__(event="*", function=None, args=[], kwargs={}, background=True)

        This method initializes the callback. Refer to the :py:meth:`libs.wireless.Receiver.onEvent` method for more information

        :param str event: the format how the event received
        :param function callback: the callback to attach
        :param list args: the unamed arguments to pass to the callback
        :param dict kwargs: the named arguments to pass to the callback
        :param bool background: if True, the callback will be executed in background

    .. py:method:: update(packet)
        
        This method updates the callback ``runnable`` attribute if the packet matches the event defined

    .. py:method:: run(packet)

        This method runs the callback if the packet matches the event defined

        :param packet: the packet to check
        :type packet: blues.libs.wireless_utils.packets.Packet



