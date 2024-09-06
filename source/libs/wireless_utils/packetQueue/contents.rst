packetQueue
==================

.. py:class:: PacketQueue 

    This class is a blues packet queue. The :py:meth:`libs.wireless.Emitter` and :py:meth:`libs.wireless.Receiver` inherit from it.

    .. py:method:: __init__(waitEmpty=False, autoStart=True)

        :param bool waitEmpty: If the queue should wait for an empty queue before stopping
        :param bool autoStart: If the queue should start automatically after initialization

    .. py:method:: isDeviceUp()

        This method returns if the device is up and links to the packetQueue

        :return: If the device is up and links to the packetQueue
        :rtype: bool

    .. py:method:: start()

        This method starts a stoppable thread (target is the :py:meth:`_task` method)

    .. py:method:: stop()

        This method stops the stoppable thread

    .. py:method:: restart()

        This method restarts the stoppable thread by stop and start method

    .. py:method:: isBusy()

        This method returns if the queue has datas

        :return: If the queue has not empty
        :rtype: bool

    .. py:method:: isEmpty()

        This method returns if the queue is empty

        :return: If the queue is empty
        :rtype: bool

    .. py:method:: _task()

        This method is implemented by ``wireless.Receiver._task`` and ``wireless.Emitter._task``

.. py:class:: StoppableThread(threading.Thread)

    This class is a subclass of :py:class:`threading.Thread`. 
    If the stop method is called, the thread is interrupted

    .. py:method:: __init__(target=None)

        :param function target: The function that will run continously in background

    .. py:method:: stop()

        Stops the thread

    .. py:method:: run()

        This method runs the function that add in the ``target``
        