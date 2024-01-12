Ultrasonic Distance Sensor
==========================

.. figure:: images/ultrasonic-1.svg
            :align: center
            :width: 60%

|

.. dropdown:: Specs (Click to Open)
    :animate: fade-in
    :color: info

    .. list-table:: Ultrasonic Specs
        :widths: 30 10 10 10
        :header-rows: 1
        :align: center

        * - Function
          - Min 
          - Nom
          - Max 
        * - Input Voltage
          - ---
          - ---
          - 5VDC
        * - Current
          - ---
          - 15mA
          - ---
        * - Range
          - 2cm
          - ---
          - 400cm
        * - Measure Angle
          - ---
          - 15˚
          - ---
        * - Frequency
          - ---
          - 40Hz
          - ---
        * - Trigger Pulse
          - ---
          - 10µs TTL
          - ---

Programming
-----------

.. tabs::
   
    .. tab:: Java

        .. code-block:: java
            :linenos:

            //import the Ultrasonic Library
            import edu.wpi.first.wpilibj.Ultrasonic;

            //Create the Ultrasonic Object
            private Ultrasonic sonar;

            //Constuct a new instance
            sonar = new Ultrasonic(Trigger, Echo);

            //Create an accessor method
            public double getDistance()
            {
                return sonar.getRangeInches();
                // or can use 
                return sonar.getRangeMM();
            }
    
        The accessor methods will then output the range in either inches or mm.

        .. note:: The valid digital pairs for Trigger and Echo pins are (Trigger, Echo) ``(0,1)``, ``(2,3)``, ``(4,5)``, ``(6,7)``, ``(8, 9)``, ``(10,11)``

    .. tab:: C++

        .. code-block:: c++
            :linenos:

            //Include the Ultrasonic Library
            #include "frc/Ultrasonic.h"

            //Constructors
            frc::Ultrasonic sonar{Trigger, Echo};

            //Create an accessor function
            double getDistance(void)
            {
                return sonar.GetRangeInches();
                // or can use 
                return sonar.GetRangeMM();
            }

        The accessor functions will then output the range in either inches or mm.  

        .. note:: The valid digital pairs for Trigger and Echo pins are (Trigger, Echo) ``(0,1)``, ``(2,3)``, ``(4,5)``, ``(6,7)``, ``(8, 9)``, ``(10,11)``