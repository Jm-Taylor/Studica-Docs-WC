Actuators
=========

The VMX Robotics Controller is capable of operating various types of actuators including those that are CAN, Digital, Ethernet, PWM, SPI, UART, or USB-based. However, this documentation only covers the actuators available on the Studica Robotics platform. If you need assistance with interfacing an actuator beyond this, you can refer to the HAL section for instructions on how to proceed.

.. grid:: 1
    :gutter: 3
    :margin: 2

    .. grid-item-card::
        :class-header: sd-bg-success sd-text-white
        :link: servo
        :link-type: doc

        Servo Motors
        ^^^

        .. figure:: images/servo-1.svg
            :align: center
            :width: 10%

    .. grid-item-card::
        :class-header: sd-bg-success sd-text-white
        :link: linear-servo
        :link-type: doc

        Linear Servo 
        ^^^

        .. figure:: images/linear-servo-1.svg
            :align: center
            :width: 40%

    .. grid-item-card::
        :class-header: sd-bg-success sd-text-white
        :link: maverick
        :link-type: doc

        Maverick DC Motor
        ^^^

        .. figure:: images/maverick-1.svg
            :align: center
            :width: 40%

.. toctree::
    :hidden:

    servo
    linear-servo
    maverick