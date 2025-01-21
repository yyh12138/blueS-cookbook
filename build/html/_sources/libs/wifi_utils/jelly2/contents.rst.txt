jelly2
============

.. py:class:: JellyDevice(wireless.Device)

    This class represents a WiFi device by JamLab-NG, which inherit the ``Device``

    .. py:method:: start8File(filename=None, loop=True)

        This method starts to jam BLE channels by configure file

        :param str filename: The filename to play
        :param bool loop: The loop to set

    .. py:method:: jam8Channels(channels, power, PSR, length)

        This method jams BLE channels

        :param list channels: The channels to jam. It ranges [1, 14]
        :param int power: The power to jam. It ranges [-128, 127]
        :param int PSR: The Packets Send Ratio to jam. It ranges (0, 1]
        :param int length: The length to jam. It ranges [0, 1500]

    .. py:method:: jamAllChannels(power, PSR, length)

        This method jams all BLE channels by ``jam8Channels``

        :param int power: The power to jam.
        :param int PSR: The Packets Send Ratio to jam.
        :param int length: The length to jam.

    



