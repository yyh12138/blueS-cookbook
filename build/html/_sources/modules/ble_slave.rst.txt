ble_slave
==============

.. py:class:: ble_slave(module.WirelessModule, interpreter.Interpreter)

    This class provides the BLE device as a slave

    .. py:method:: init()

        Initialize the BLE slave

        :args: 
            - INTERFACE: "hci0"
            - ATT_FILE: ""
            - GATT_FILE: "/tmp/gatt.cfg"
            - SCENARIO: ""

    .. py:method:: prerun()

        This method inits the interpreter and regists the CMD, such as ``clear``, ``exit``, ``show``, ``load``, ``notification``, ``disconnect``, ``advertising``, ``address``, ``pairing`` 

    .. py:method:: clear()

        Clear the screen

    .. py:method:: exit()

        Exit the BLE slave interpreter
    
    .. py:method:: load(filename)

        This method inits the GATT server, then imports the ATT and GATT from the .cfg file, final add attributes to the GATT server

    .. py:method:: disconnect()
            
        Disconnect the BLE slave device
    
    .. py:method:: show()

        Show the ATT and GATT from .cfg file

    .. py:method:: notification()

        Send a notification (``BLEHandleValueNotification``) to the BLE master

    .. py:method:: advertising(address="")

        This method sets or get address of the BLE slave

        :param str address: The address of the BLE slave

    .. py:method:: address(type="ADV_IND", data, scanData, intervalMin="200", intervalMax="210")

        This method starts advertising by excuting ``ble_adv``

        :param str type: The type of the advertising
        :param bytes data: The data of the advertising
        :param bytes scanData: The scan data of the advertising
        :param str intervalMin: The minimum interval of the advertising
        :param str intervalMax: The maximum interval of the advertising

    .. py:method:: pairing(active="active", paramters="")

        This method starts pairing by excuting ``ble_pair``

        :param str active: The active of the pairing
        :param str paramters: The paramters of the pairing

    .. py:method:: run()

        This method inits the BLE slave and enter into interpreter loop

     

    