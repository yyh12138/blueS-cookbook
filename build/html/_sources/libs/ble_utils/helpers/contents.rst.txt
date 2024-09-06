helpers
================

This module helps to manipulate BLE link layer packets.

.. py:method:: frequentToChannel(frequency)

    Convert frequency to channel number.

    :param int frequency: Frequency in MHz.
    :return: Channel number.
    :rtype: int
    :Example:
        >>> frequentToChannel(2402)
        37

.. py:method:: channelToFrequent(channel)

    Convert channel number to frequency.

    :param int channel: Channel number.
    :return: Frequency in MHz.
    :rtype: int
    :Example:
        >>> channelToFrequent(37)
        2402

.. py:method:: crc24(data, length, init=0x555555)

    Calculate CRC24 of the given data.

    :param bytes data: Data to calculate CRC24.
    :param int length: Length of the data.
    :param int init: Initial value of the CRC24.
    :return: CRC24 value.
    :rtype: bytes
    :Example:
        >>> data = bytes.fromhex("0215110006000461ca0ce41b1e430559ac74e382667051")
        >>> crc24(data, len(data)).hex()
        "545d96"

.. py:method:: isAccessAddress(aa)

    Check if the given value is an access address

    - bits cannot be all 0 or all 1
    - every 6 bits cannot be all 0 or all 1
    - last 2 bits cannot be all 1

    :param int aa: Value to check.
    :return: True if the value is an access address, False otherwise.
    :rtype: bool
    :Example:
        >>> isAccessAddress(0x8E89BED6)
        True

.. py:method:: rssiToDbm(rssi)

    Convert RSSI to dBm

    :param int rssi: RSSI value
    :return: RSSI in dBm
    :rtype: float
    :Example:
        >>> rssiToDbm(12)
        -45.0

.. py:method:: dewhiten(data, channel)

    De-whiten the given raw data according to channel value

    :param bytes data: Raw data to de-whiten
    :param int channel: Channel number
    :return: De-whitened data
    :rtype: bytes