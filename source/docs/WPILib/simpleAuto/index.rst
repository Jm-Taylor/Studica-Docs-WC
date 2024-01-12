Simple Auto Example
===================

.. note:: It's best to download the example and follow along. The example project can be donwloaded `here <https://github.com/studica/WorldSkills-Example-Projects/tree/main/Simple%20Auto>`__.

Sometimes getting into something new can be hard. With this example as a stepping stone it will hopefully become more clear to most. 

.. grid:: 2
    :gutter: 3
    :margin: 2

    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: constants
        :link-type: doc

        1 - Constants.java
        ^^^

        Constants class

    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: drivetrain
        :link-type: doc

        2 - DriveTrain.java
        ^^^

        DriveTrain subsystem class
    
    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: auto-command
        :link-type: doc

        3 - AutoCommand.java
        ^^^

        Auto command wrapper for sequential autos

    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: simple-drive
        :link-type: doc

        4 - SimpleDrive.java
        ^^^

        SimpleDrive Command class that calls the drivetrain subsystem

    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: drive-motor
        :link-type: doc

        5 - DriveMotor.java
        ^^^

        Acutal command that will drive the motor

    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: robot-container
        :link-type: doc

        6 - RobotContainer.java
        ^^^

        Robot Container of instances

    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: robot
        :link-type: doc

        7 - Robot.java
        ^^^

        Main methods of project

    .. grid-item-card::
        :class-header: sd-bg-dark sd-text-white
        :link: running-auto
        :link-type: doc

        8 - Deploying and Running Autonomous
        ^^^

        Deploy code to the robot and run the code using Control Station.

.. toctree::
    :hidden:

    constants 
    drivetrain
    auto-command
    simple-drive
    drive-motor
    robot-container
    robot
    running-auto