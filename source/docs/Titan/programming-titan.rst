Programming the Titan
=====================

Motor Setup
-----------

.. tabs::

    .. tab:: Java

        .. code-block:: java
            :linenos:

            //import the TitanQuad Library
            import com.studica.frc.TitanQuad;

            //Create the TitanQuad Object
            private TitanQuad motor;

            //Constuct a new instance
            motor = new TitanQuad(TITAN_CAN_ID, TITAN_MOTOR_NUMBER);
    
        .. note:: ``TITAN_CAN_ID`` is the CAN id for the Titan, by defualt it is 42. ``TITAN_MOTOR_NUMBER`` is the motor port to be used. Valid range is ``0 - 3``, this corresponds to the M0 - M3 on the Titan. 

    .. tab:: C++ (Header)

        .. code-block:: c++
            :linenos:

            //Include the TitanQuad Library
            #include <studica/TitanQuad.h>

            //Constuct a new instance
            private:
                studica::TitanQuad motor{TITAN_CAN_ID, TITAN_MOTOR_NUMBER};
        
        .. note:: ``TITAN_CAN_ID`` is the CAN id for the Titan, by defualt it is 42. ``TITAN_MOTOR_NUMBER`` is the motor port to be used. Valid range is ``0 - 3``, this corresponds to the M0 - M3 on the Titan.

Setting Motor Speed
-------------------

.. tabs::

    .. tab:: Java

        .. code-block:: java
            :linenos:

            /**
             * Sets the speed of a motor
             * <p>
             * @param speed range -1 to 1 (0 stop)
             */
            public void setMotorSpeed(double speed)
            {
                motor.set(speed);
            }

    .. tab:: C++ (Source)

        .. code-block:: c++
            :linenos:

            /**
             * Sets the speed of a motor
             * <p>
             * @param speed range -1 to 1 (0 stop)
             */
            void Example::SetMotorSpeed(double speed)
            {
                motor.Set(speed);
            } 

Encoder Setup
-------------

Encoder setup code for when the encoders are plugged into the Titan and not the VMX.

.. tabs::

    .. tab:: Java

        .. code-block:: java
            :linenos:

            package frc.robot.subsystems;

            //Subsystem Base import
            import edu.wpi.first.wpilibj2.command.SubsystemBase;

            //Titan import
            import com.studica.frc.TitanQuad;

            //Titan Encoder import
            import com.studica.frc.TitanQuadEncoder;

            public class Example extends SubsystemBase
            {
                /**
                 * Motors
                 */
                private TitanQuad motor;

                /**
                 * Encoders
                 */
                private TitanQuadEncoder encoder; 

                public Example()
                {
                    //Motors
                    motor = new TitanQuad(TITAN_CAN_ID, TITAN_MOTOR_NUMBER);

                    //Encoder   
                    encoder = new TitanQuadEncoder(motor, TITAN_MOTOR_NUMBER, TICKS_PER_REV);
                }
            }

        .. note:: ``motor`` is the TitanQuad motor object that was created before. ``TITAN_MOTOR_NUMBER`` is the motor number the encoder is plugged into. ``TICKS_PER_REV`` is the distance traveled per tick of the encoder. Refer to the Encoder section in Sensors to understand more.

    .. tab:: C++ (Header)

        .. code-block:: c++
            :linenos:

            //Include the TitanQuad and TitanQuadEncoder Library
            #include <studica/TitanQuad.h>
            #include <studica/TitanQuadEncoder.h>

            //Constuct a new instance
            private:
                studica::TitanQuad motor{TITAN_CAN_ID, TITAN_MOTOR_NUMBER};
                studica::TitanQuadEncoder encoder{motor, TITAN_MOTOR_NUMBER, TICKS_PER_REV};
        
        .. note:: ``motor`` is the TitanQuad motor object that was created before. ``TITAN_MOTOR_NUMBER`` is the motor number the encoder is plugged into. ``TICKS_PER_REV`` is the distance traveled per tick of the encoder. Refer to the Encoder section in Sensors to understand more. 

Motor and Encoder Flags 
-----------------------

There are some motor and encoder flags that can be set to ensure smooth operations. Its best for these flags to be set in the constructor.

.. tabs::

    .. tab:: Java

        .. code-block:: java
            :linenos:

            package frc.robot.subsystems;

            //Subsystem Base import
            import edu.wpi.first.wpilibj2.command.SubsystemBase;

            //Titan import
            import com.studica.frc.TitanQuad;

            //Titan Encoder import
            import com.studica.frc.TitanQuadEncoder;

            public class Example extends SubsystemBase
            {
                /**
                 * Motors
                 */
                private TitanQuad motor;

                /**
                 * Encoders
                 */
                private TitanQuadEncoder encoder; 

                public Example()
                {
                    //Motors
                    motor = new TitanQuad(TITAN_CAN_ID, TITAN_MOTOR_NUMBER);

                    //Encoder
                    encoder = new TitanQuadEncoder(motor, TITAN_MOTOR_NUMBER, TICKS_PER_REV);

                    //Motor Flags
                    motor.setInverted(false); // Set to true to invert motor ouput 
                    motor.invertRPM(); // Invert the RPM count when the encoder is plugged in

                    //Encoder Flags
                    encoder.setReverseDirection(); // Will reverse the encoder count direction 
                }
            }

    .. tab:: C++ (Source)

        .. code-block:: c++
            :linenos:

            //Include Header
            #include "subsystems/Example.h"

            void Example::Example()
            {
                // Motor flags
                motor.SetInverted(false); // Set true to invert motor output
                motor.InvertRPM(); // Inverts the RPM count when the encoder is plugged in

                // Encoder flags
                encoder.SetReverseDirection(); // Will reverse the encoder count direction
            }

Full Example
------------

.. tabs::
   
    .. tab:: Java

        .. code-block:: java
            :linenos:

            package frc.robot.subsystems;

            //Subsystem Base import
            import edu.wpi.first.wpilibj2.command.SubsystemBase;

            //Titan import
            import com.studica.frc.TitanQuad;

            //Titan Encoder import
            import com.studica.frc.TitanQuadEncoder;

            public class Example extends SubsystemBase
            {
                /**
                 * Motors
                 */
                private TitanQuad motor;

                /**
                 * Encoders
                 */
                private TitanQuadEncoder encoder; 

                public Example()
                {
                    //Motors
                    motor = new TitanQuad(TITAN_CAN_ID, TITAN_MOTOR_NUMBER);

                    //Encoder
                    encoder = new TitanQuadEncoder(motor, TITAN_MOTOR_NUMBER, TICKS_PER_REV);

                    //Motor Flags
                    motor.setInverted(false); // Set to true to invert motor ouput 
                    motor.invertRPM(); // Invert the RPM count when the encoder is plugged in

                    //Encoder Flags
                    encoder.setReverseDirection(); // Will reverse the encoder count direction 
                }

                /**
                 * Sets the speed of a motor
                 * <p>
                 * @param speed range -1 to 1 (0 stop)
                 */
                public void setMotorSpeed(double speed)
                {
                    motor.set(speed);
                }
            }
            

    .. tab:: C++ (Header)

        .. code-block:: c++
            :linenos:

            #pragma once

            //Include SubsystemBase
            #include <frc2/command/SubsystemBase.h>

            //Include the TitanQuad and TitanQuadEncoder Library
            #include <studica/TitanQuad.h>
            #include <studica/TitanQuadEncoder.h>

            class Example : public frc2::SubsystemBase
            {
                public:
                    Example();
                    void SetMotorSpeed(double speed);

                private:
                    studica::TitanQuad motor(TITAN_CAN_ID, TITAN_MOTOR_NUMBER);
                    studica::TitanQuadEncoder encoder{motor, TITAN_MOTOR_NUMBER, TICKS_PER_REV};
            };
    
    .. tab:: C++ (Source)

            .. code-block:: c++
                :linenos:
    
                //Include Header
                #include "subsystems/Example.h"

                //Constructor
                Example::Example()
                {
                    // Motor flags
                    motor.SetInverted(false); // Set true to invert motor output
                    motor.InvertRPM(); // Inverts the RPM count when the encoder is plugged in

                    // Encoder flags
                    encoder.SetReverseDirection(); // Will reverse the encoder count direction
                }

                /**
                 * Sets the speed of a motor
                 * <p>
                 * @param speed range -1 to 1 (0 stop)
                 */
                void Example::SetMotorSpeed(double speed)
                {
                    motor.Set(speed);
                }        