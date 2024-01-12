Control Station
===============

Control Station Console is used for enabling, disabling, selecting operation mode and for sending controller inputs to the robot. It will also autoconfigure Shuffleboard and launch it correctly for you. 

Download
--------

.. note:: The latest version of control station console was compiled on Win10. While it may work on Win11 there is no guarantees that it will work correctly 100% of the time. 

.. grid:: 1
    :gutter: 1
    :margin: 2

    .. grid-item-card::
        :class-header: sd-bg-success sd-text-white
        :link: https://www.studica.com/downloads/Studica-Robotics/FRC-WSR/ControlStation/ControlStationConsole-Setup.zip
        :link-type: url

        Download Control Station Console
        ^^^

        Click to download the latest version of control station console.

|

.. dropdown:: Installing (Click to Open)
    :animate: fade-in
    :color: info

    Once downloaded, run the :bdg-danger-line:`ControlStationConsole-Setup.exe` after extracting the zip. 

    .. figure:: images/installation-1.png
            :align: center
            :width: 50%
    
    |

    The install will then run through the license agreement, and you can choose your installation path.

    .. figure:: images/installation-2.png
            :align: center
            :width: 50%
    
    |

    The install will now install on your computer. It will be complete when you see this page.

    .. figure:: images/installation-3.png
            :align: center
            :width: 50%

.. dropdown:: Using the Control Station Console
    :animate: fade-in
    :color: info

    To start using the control station console open the :bdg-danger-line:`Control Station Console.exe` on your desktop or start menu.

    .. figure:: images/operation-1.png
            :align: center
            :width: 60%

    |

    The console will ask you to enter your robots IP address. If your team number is :bdg-danger-line:`1234` then using the format :bdg-danger-line:`10.xx.xx.2` your IP address will be :bdg-danger-line:`10.12.34.2`. If you have an ethernet connection to the robot the IP address will be :bdg-danger-line:`172.22.11.2`.

    .. figure:: images/operation-2.png
            :align: center
            :width: 60%

    |

    The console will then connect the Shuffleboard key to your IP address and launch Shuffleboard for you. 

    .. figure:: images/operation-3.png
            :align: center
            :width: 60%

    |

    1. Battery Voltage Indicator - This will tell you the current voltage of the battery. When the battery starts to approach 11.5V it is time to replace with a charged battery. 

    2. Robot Current State - This is the state indicator for the robot. As pictured the robot is in Teleoperated and is Disabled. When the robot is enabled you will see a :bdg-danger-line:`Teleoperated Enabled` status instead. 

    3. IP Address you punched in and what is being used.

    4. Quit (q) - press :bdg-danger-line:`q` on the keyboard to quit. 

    5. Set enabled (e,d) - press :bdg-danger-line:`e` to enable the robot and press :bdg-danger-line:`d` to disable the robot. 

    6. Set Control Mode (o,a,t) - Sets the control mode, currently as pictured the console is in Teleoperated mode.

       - **o** is Teleoperated
       - **a** is Autonomous
       - **t** is Test

    7. Status Indicators - These are some flags to show you that connections are present. There are three flags :bdg-danger-line:`Robot Comms`, :bdg-danger-line:`Robot Code`, and :bdg-danger-line:`Joysticks`. 

       - **Robot Comms** will indicate that the console is talking with the robot.
       - **Robot Code** will indicate that there is valid code running on the robot.
       - **Joysticks** will indicate that there is a joystick plugged in.  