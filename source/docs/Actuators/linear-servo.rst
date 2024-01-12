Linear Servo
============

A linear servo acts the same as a standard servo but in a linear movement instead of rotational. There are two sizes of linear servos with two different speed and torque values. 

.. figure:: images/linear-servo-1.svg
        :align: center
        :width: 60%

|

.. dropdown:: Linear Servo Specifications (Click to Open)
    :animate: fade-in
    :color: info

    .. list-table:: Control Specs
        :widths: 40 40
        :header-rows: 1
        :align: center

        * - Function
          - Value
        * - Control Signal
          - PWM
        * - Frequency
          - 50 Hz
        * - Motor Voltage
          - 6VDC
        * - Signal Voltage
          - 5VDC
        * - Wire Length
          - 340mm
        * - Connector
          - 2.54mm Dupont 3-Pin Female
        * - Operating Temperature
          - -10˚C ~+50˚C
        * - Storage Temperature
          - -10˚C ~+50˚C          

    .. list-table:: Mechanical Specs
        :widths: 40 10 10 10 10
        :header-rows: 1
        :align: center

        * - Function
          - 50mm 50N
          - 50mm 200N
          - 140mm 50N
          - 140mm 200N
        * - Stroke Length
          - 50mm
          - 50mm
          - 140mm
          - 140mm  
        * - Gear Ratio 
          - 63:1
          - 150:1
          - 63:1
          - 150:1 
        * - No Load Speed 
          - 13mm/s
          - 6mm/s 
          - 13mm/s 
          - 6mm/s 
        * - No Load Current
          - 150mA
          - 150mA 
          - 150mA
          - 150mA     
        * - Max Efficiency Point Load
          - 30N
          - 75N 
          - 30N
          - 75N  
        * - Max Efficiency Point Speed
          - 11mm/s
          - 5mm/s 
          - 11mm/s
          - 5mm/s  
        * - Max Efficiency Point Current
          - 360mA
          - 360mA 
          - 360mA
          - 360mA    
        * - Peak Power Point Load
          - 66N
          - 170N 
          - 66N
          - 170N 
        * - Peak Power Point Speed
          - 8mm/s
          - 3.3mm/s 
          - 8mm/s
          - 3.3mm/s  
        * - Peak Power Point Current
          - 560mA
          - 560mA 
          - 560mA
          - 560mA  
        * - Max Force Load
          - 95N
          - 190N
          - 95N
          - 190N
        * - Max Force Speed
          - 5mm/s
          - 2.5mm/s
          - 5mm/s
          - 2.5mm/s 
        * - Max Force Current
          - 850mA
          - 820mA 
          - 850mA
          - 820mA 
        * - Stall Torque
          - 150N
          - 325N
          - 150N
          - 325N 
        * - Stall Current
          - 1A
          - 1A 
          - 1A
          - 1A  
        * - Max Static Force
          - 100N
          - 190N 
          - 100N
          - 190N 
        * - Weight
          - 65g
          - 65g
          - 96g
          - 96g
        * - Stroke Repeatablility
          - ±0.5mm
          - ±0.5mm 
          - ±0.5mm
          - ±0.5mm
        * - Max Side Load 
          - 10N 
          - 10N
          - 10N
          - 10N

|

Programming
-----------

Programming the Linear Servo is similar to the standard servo however, the pulse width range must change. A standard servo operates with a range of 500µs to 2500µs. A linear servo has a rough range of ~800µs to 2200µs. We say rough range as every linear servo is a bit different (tolearnces). 

.. tabs::

    .. tab:: Java

        .. code-block:: java
            :linenos:

            //import the Servo Library
            import com.studica.frc.Servo;

            //Create the Servo Object
            private Servo servo;

            //Constuct a new instance
            servo = new Servo(port);

            /**
             * Modify the Pulse Width Range
             * 
             * Parameters:
             *     - max: The max PWM pulse width in ms (2.1 in example)
             *     - deadbandMax: The high end of the deadband range pulse width in ms (2.1 in example)
             *     - center: The center pulse width in ms (1.5 in example)
             *     - deadbandMin: The low end of the deadband range pulse width in ms (0.95 in example)
             *     - min: The minimum pulse width in ms (0.9 in example)
             */     
            servo.setBounds(2.1, 2.1, 1.5, 0.95, 0.9);

            //Can then use this mutator to set the linear servo position
            servo.setPosition(position); //Range 0 - 1, 0 being fully retracted and 1 being fully extended
    
        The mutator method will allow you to set the distance travel of the linear servo.

    .. tab:: C++

        .. code-block:: c++
            :linenos:

            //Include the Servo Library
            #include "studica/Servo.h"

            //Constructor
            studica::Servo servo{port};

            /**
             * Modify the Pulse Width Range
             * 
             * Parameters:
             *     - max: The max PWM pulse width in ms (2.1 in example)
             *     - deadbandMax: The high end of the deadband range pulse width in ms (2.1 in example)
             *     - center: The center pulse width in ms (1.5 in example)
             *     - deadbandMin: The low end of the deadband range pulse width in ms (0.95 in example)
             *     - min: The minimum pulse width in ms (0.9 in example)
             */     
            servo.SetBounds(2.1, 2.1, 1.5, 0.95, 0.9);

            //Use this function to set the linear servo position
            servo.SetPosition(position); //Range 0 - 1, 0 being fully retracted and 1 being fully extended

        The function will allow you to set the distance travel of the linear servo.

|

Calibration
^^^^^^^^^^^

To calibrate the linear servo and find the correct pulse width range for the bounds function a trial and error test is required. 

1. Start with the linear servo fully retracted.
2. Set the minimum pulse width range to as low as possible (0.8) is a good starting point. Make sure the deadbandMin is the same as the min value for calibration. This can be adjusted later at your own descreation.  
3. Start moving the linear servo with servo.setPosition(0.2); If the servo does not move increase the min number and repeat. If it does move, go to the next step. 
4. Set the servo.setPosition(0); The servo should fully retract. If it does not lower or raise the min pulse value until it does. When complete repeat step 3 and 4 to ensure repeatablility.
5. Set the max pulse width range to around 1.9. Make sure the deadbandMax is the same value.
6. Move the linear servo with servo.setPosition(1); The servo will move as far as it can. Using a ruler verify if the linear servo has fully extended 50mm or 140mm based on the servo. If it has not slowly increase the max and deadbandMax until it does. 
7. Verify that the servo will fully retract and extend without issue by using servo.setPosition(0); and servo.setPosition(1); If not repeat the steps above.

.. note:: Going outside the bounds of the linear servo will produce weird results. A slow and proper calibration will yield the best results. 