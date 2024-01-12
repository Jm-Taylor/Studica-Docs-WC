Autonomous Basics
=================

The basics of autonomous with WPILib. 

Command Groups
--------------

Command groups are simple way to pair multiple commands together to create an autonomous routine. 

Sequential Command Group
^^^^^^^^^^^^^^^^^^^^^^^^

    The most popular of the command groups, :bdg-danger-line:`SequentialCommandGroup` will run a list of commands in sequential order. Starting with the first command in the list then the second and so on.

    .. warning:: The **SequentialCommandGroup** will not finish unless all the commands finish. Also if a command in the list does not finish the next command in line will not start.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                import edu.wpi.first.wpilibj2.command.SequentialCommandGroup;

                public class Example extends SequentialCommandGroup
                {
                    public Example()
                    {
                        addCommands
                        (
                            //Drive Forward
                            new DriveForward(),

                            //Drive Reverse
                            new DriveReverse()
                        );
                    }
                }

        .. tab:: C++

            **Header**

            .. code-block:: c++
                :linenos:

                #prama once

                #include <frc2/command/CommandHelper.h>
                #include <frc2/command/SequentialCommandGroup.h>

                class Example
                    : public frc2::CommandHelper<frc2::SequentialCommandGroup, Example>
                {
                    public:
                        Example(void);
                };

            **Source**

            .. code-block:: c++
                :linenos:

                #include "commands/Example.h"

                Example::Example(void)
                {
                    AddCommands
                    (
                        //Drive Forward
                        DriveForward(),

                        //Drive Backwards
                        DriveReverse()
                    );
                }

    In the above example using :bdg-danger-line:`SequentialCommandGroup` the command :bdg-danger-line:`DriveForward()` will be executed first and when complete the command :bdg-danger-line:`DriveReverse()` will be executed.

    .. caution:: If :bdg-danger-line:`DriveForward()` does not end :bdg-danger-line:`DriveReverse()` will never start.

Parallel Command Group
^^^^^^^^^^^^^^^^^^^^^^

    The :bdg-danger-line:`ParallelCommandGroup` is just like the :bdg-danger-line:`SequentialCommandGroup` except that all the commands run at the same time. The command group will only finish when all commands are finished. 

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                import edu.wpi.first.wpilibj2.command.ParallelCommandGroup;

                public class Example extends ParallelCommandGroup
                {
                    public Example()
                    {
                        addCommands
                        (
                            //Drive Forward
                            new DriveForward(),

                            //Move Arm to Home Position
                            new Arm(Pos.Home)
                        );
                    }
                }

        .. tab:: C++ 

            **Header**

            .. code-block:: c++
                :linenos:

                #prama once

                #include <frc2/command/CommandHelper.h>
                #include <frc2/command/ParallelCommandGroup.h>

                class Example
                    : public frc2::CommandHelper<frc2::ParallelCommandGroup, Example>
                {
                    public:
                        Example(void);
                };

            **Source**

            .. code-block:: c++
                :linenos:

                #include "commands/Example.h"

                Example::Example(void)
                {
                    AddCommands
                    (
                        //Drive Forward
                        DriveForward(),

                        //Arm to Home Position
                        Arm(Pos::Home)
                    );
                }

    In the above example using :bdg-danger-line:`ParallelCommandGroup` the commands :bdg-danger-line:`DriveForward()` and :bdg-danger-line:`Arm(Pos.Home)` will be executed at the same time.

    .. caution:: **Both** :bdg-danger-line:`DriveForward()` **and** :bdg-danger-line:`Arm(Pos.Home)` **MUST** complete to move on. If they do not complete the routine will be stuck at the example() call. 

Parallel Race Group
^^^^^^^^^^^^^^^^^^^

    The :bdg-danger-line:`ParallelRaceGroup` is similar to the :bdg-danger-line:`ParallelCommandGroup` except that a race condition is created. All commands start at the same time but, when one command is finished it interrupts all other commands running and ends the command group.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                import edu.wpi.first.wpilibj2.command.ParallelRaceGroup;

                public class Example extends ParallelRaceGroup
                {
                    public Example()
                    {
                        addCommands
                        (
                            //Drive Forward
                            new DriveForward(),

                            //Move Arm to Home Position
                            new Arm(Pos.Home)
                        );
                    }
                }

        .. tab:: C++ 

            **Header**

            .. code-block:: c++
                :linenos:

                #prama once

                #include <frc2/command/CommandHelper.h>
                #include <frc2/command/ParallelRaceGroup.h>

                class Example
                    : public frc2::CommandHelper<frc2::ParallelRaceGroup, Example>
                {
                    public:
                        Example(void);
                };

            **Source**

            .. code-block:: c++
                :linenos:

                #include "commands/Example.h"

                Example::Example(void)
                {
                    AddCommands
                    (
                        //Drive Forward
                        DriveForward(),

                        //Arm to Home Position
                        Arm(Pos::Home)
                    );
                }
    
    In the above example using :bdg-danger-line:`ParallelRaceGroup` the commands :bdg-danger-line:`DriveForward()` and :bdg-danger-line:`Arm(Pos.Home)` will be executed at the same time. 

    .. note:: If :bdg-danger-line:`DriveForward()` or :bdg-danger-line:`Arm(Pos.Home)` completes before the other then the other will be interrupted and stop running.

Java Only Benefits
^^^^^^^^^^^^^^^^^^

    For Java only, *Static Factory Methods* are possible, allowing a much simplar way to declare command groups.

sequence()
~~~~~~~~~~

    The :bdg-danger-line:`sequence()` static method allows for a sequential command group.

parallel()
~~~~~~~~~~

    The :bdg-danger-line:`parallel()` static method allows for a parallel command group.

race()
~~~~~~

    The :bdg-danger-line:`race()` static method allows for a parallel race group.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                import edu.wpi.first.wpilibj2.command.SequentialCommandGroup;

                public class Example extends SequentialCommandGroup
                {
                    public Example()
                    {
                        addCommands
                        (
                            race(new DriveForward(), new ElevatorUP()),
                            parallel(new ShootObject(), new LineupGoal()),
                            sequence(new DriveReverse(), new StrafeRight())
                        );
                    }
                }

    If we analyze this command group we can break down what is happening. 

    1. We have :bdg-danger-line:`race(new DriveForward(), new ElevatorUP())` this will create a :bdg-danger-line:`ParallelRaceGroup` that has the two commands :bdg-danger-line:`DriveForward()` and :bdg-danger-line:`ElevatorUP()` run at the same time in a race. When **one** finishes it will stop the other.
    2. As the main command group is the :bdg-danger-line:`SequentialCommandGroup` we then move on to the next command which is a :bdg-danger-line:`ParallelCommandGroup`.
    3. The :bdg-danger-line:`ParallelCommandGroup` of :bdg-danger-line:`parallel(new ShootObject(), new LineupGoal())` tells us that :bdg-danger-line:`ShootObject()` and :bdg-danger-line:`LineupGoal()` happen at the same time. When **both** are complete it will pass to the next command group. 
    4. The last command group here is the :bdg-danger-line:`sequence(new DriveReverse(), new StrafeRight())` which is also a :bdg-danger-line:`SequentialCommandGroup`. This group is telling the robot to :bdg-danger-line:`DriveReverse()` and when that is done to :bdg-danger-line:`StrafeRight()`. 

Conditional Command
-------------------

    The :bdg-danger-line:`ConditionalCommand` will run one command or another based on condition that must be met.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                // Base parameters
                new ConditionalCommand(trueCommand, falseCommand, boolean condition);

                // Use case
                new ConditionalCommand(new DriveForward(), new DriveReverse(), isLimitHit());

        .. tab:: C++

            .. code-block:: c++
                :linenos:

                frc2::ConditionalCommand(trueCommand, falseCommand, [&limit] {return isLimitHit();});

Wait Command
------------

    The :bdg-danger-line:`WaitCommand()` is useful for when a timed wait period is required.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                // Waits 10 seconds
                new WaitCommand(10);

        .. tab:: C++

            .. code-block:: c++
                :linenos:

                // Waits 10 seconds
                frc2::WaitCommand(10.0_s);

Wait Until Command
------------------

    The :bdg-danger-line:`WaitUntilCommand` is an upgraded version of :bdg-danger-line:`WaitCommand()` as a boolean condition can be added.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                // Waits 10 seconds
                new WaitUntilCommand(10);

                // Waits for limit switch to be true
                new WaitUntilCommand(isLimitHit());

        .. tab:: C++

            .. code-block:: c++
                :linenos:

                // Waits 10 seconds
                frc2::WaitUntilCommand(10.0_s);

                // Waits for limit switch to be true
                frc2.WaitUntilCommand([&Limit] {return isLimitHit();});

Command Decorators
------------------

    Command decorators take the base command and add additonal functionalities to it.

withTimeout()
^^^^^^^^^^^^^

    Adds a timeout to the command. When the timeout expires the command will be interrupted and end.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                // Add a 10 second timeout
                new command.withTimeout(10);

        .. tab:: C++

            .. code-block:: c++
                :linenos:

                // Add a 10 second timeout
                command.WithTimeout(10.0_s);

withInterrupt()
^^^^^^^^^^^^^^^

    Adds a condition that will interrupt the command.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                new command.withInterrupt(isLimitHit());

        .. tab:: C++

            .. code-block:: c++
                :linenos:

                command.WithInterrupt([&limit]{return isLimitHit();});

andThen()
^^^^^^^^^

    Adds a method that is executed after the command ends.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                new command.andThen(() -> System.out.println("Command Finished"););

        .. tab:: C++

            .. code-block:: c++
                :linenos:

                command.AndThen([] {std::cout<<"Command Finished";});

beforeStarting()
^^^^^^^^^^^^^^^^

    Adds a method that is executed before the command starts.

    .. tabs::

        .. tab:: Java

            .. code-block:: java
                :linenos:

                new command.beforeStarting(() -> System.out.println("Command Starting"););

        .. tab:: C++

            .. code-block:: c++
                :linenos:

                command.BeforeStarting([] {std::cout<<"Command Starting"});

