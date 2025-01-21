ble_jam
================

.. py:class:: ble_jam(module.WirelessModule)

    This class jam the BLE connection by WiFi

    .. py:method:: init()

        This method will initialize the BLE jam module.

        ``mon0`` needs to be set in monitor mode before running this module by using nexutil. Check by using ``ifconfig``.

        ``POWER`` is the power level of the jamming signal. It ranges [-128, 127].

        ``LENGTH`` is the length of the jamming packet. It ranges [0, 1500].

        ``PSR`` is the packet send rate. It ranges (0, 1].

        ``CONF_FILE`` is the configuration file for the BLE jam module in order to more detailed operating.

        :args:
            - INTERFACE: "mon0"
            - POWER: "120"
            - LENGTH: "1200"
            - PSR: "1"
            - CONF_FILE: "/root/blueS/blues/libs/wifi_utils/jelly.conf"

    .. py:method:: run()

        This method will start the BLE jam module by excuting ``jamAllChannels``.
