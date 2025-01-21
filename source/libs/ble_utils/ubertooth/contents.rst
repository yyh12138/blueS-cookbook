ubertooth
==================
.. py:class:: BLEUbertoothDevice(BtUbertoothDevice)

    This class represents a BLE device by Ubertooth, which inherit the ``BtUbertoothDevice``

    .. py:method:: getAccessAddress()

        This method gets the access address of the BLE device

    .. py:method:: setSweepingMode(enable=True, sequence=[37,38,39])

        This method sets the sweeping mode of the Ubertooth device. It allows to provide a subset of advertising channels to monitor sequentially
        
        :param bool enable: Enable or disable the sweeping mode
        :param list sequence: The sequence of the channels to sweep

    .. py:method:: setJamming(enable=True)

        This method sets the jamming mode of the Ubertooth device.
        
        :param bool enable: Enable or disable the jamming mode

    .. py:method:: restartSniffingMode()

        This method restarts the sniffing mode of the Ubertooth device by ``sniffNewConnections`` or ``sniffExistingConnections``

    .. py:method:: sniffAdvertisements(address="00:00:00:00:00:00", channel=None)

        This method sniffs the advertisements of the BLE device

        :param str address: The address of the BLE device
        :param int channel: The channel of the BLE device

    .. py:method:: sniffNewConnections(address="00:00:00:00:00:00", channel=None)

        This method sniffs the new connections of the BLE device

        :param str address: The address of the BLE device
        :param int channel: The channel of the BLE device

    .. py:method:: sniffExistingConnections(accessAddress=None, crcInit=None, channelMap=None)

        This method sniffs the existing connections of the BLE device

        :param int accessAddress: The access address of the BLE device
        :param int crcInit: The CRC initialization value of the BLE device
        :param int channelMap: The channel map of the BLE device

    .. py:method:: setScan(enable=True)

        This method sets the scanning mode of the Ubertooth device
        
        :param bool enable: Enable or disable the scanning mode

    .. py:method:: recv()

        This method receives and returns the data from the Ubertooth device