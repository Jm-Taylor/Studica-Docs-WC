Creating a Project
==================

.. important:: When creating a project for the first time internet connection is required. 

.. note:: Before creating a C++ project for the first time on a brand new computer, create a java project first. The C++ project creation seems to rely on a java dependecy. 

.. tabs::

    .. tab:: Java

        Open the appropriate VS Code ``FRC VS Code 2020`` and hit ``Ctrl + Shift + P`` or ``F1`` to open the the command palette. In the command palette search for the command ``WPILib: Create a new project``.

        .. figure:: images/java/creating-a-project-1.png
            :align: center

        |

        The project creation window will open up.

        .. figure:: images/java/creating-a-project-2.png
            :align: center

        |

        1. Start by clicking on the *Select a project type(Example or Template)* button and select ``template``
        2. Choose a programming language by selecting the *Select a language* button. In this case ``Java``
        3. For *Select a project base*, select ``Command Robot``
        4. Choose a folder location to store the project
        5. Enter an appropriate project name
        6. Enter your team number

        An example of a filled out project creator is shown below.

        .. figure:: images/java/creating-a-project-3.png
            :align: center

        |

        Hit *Generate Project* to finalize the creation of the project. There will be a prompt as shown to open in a new window or the current window. A new window will open another instance of VS Code whereas the current window will close the any open project you have and place this project in the currently opened VS Code window.

        .. figure:: images/java/creating-a-project-4.png
            :align: center

        |

        .. note:: The project will then automatically build for the first time. If the build is not successful, either VS Code and WPILib was installed incorrectly or you are not connected to the internet.

        The VS Code window should now look like this and a Java project has been created!

        .. figure:: images/java/creating-a-project-5.png
            :align: center

        |

        .. important:: After creating a project it is always a good idea to run the ``Change the deploy target to VMX-Pi (from RoboRIO)`` command from the VMX-Pi WPILib extension. 

    .. tab:: C++

        .. note:: A computers ``anti-virus`` sometimes interferes with c++ projects, it is a good idea to have it disabled while working on code, compiling and deploying. 

        Open the appropriate VS Code ``FRC VS Code 2020`` and hit ``Ctrl + Shift + P`` or ``F1`` to open the the command palette. In the command palette search for the command ``WPILib: Create a new project``.

        .. figure:: images/c++/creating-a-project-1.png
            :align: center

        |

        The project creation window will open up.

        .. figure:: images/c++/creating-a-project-2.png
            :align: center

        |

        1. Start by clicking on the *Select a project type(Example or Template)* button and select ``template``
        2. Choose a programming language by selecting the *Select a language* button. In this case ``cpp``
        3. For *Select a project base*, select ``Command Robot``
        4. Choose a folder location to store the project
        5. Enter an appropriate project name
        6. Enter your team number

        An example of a filled out project creator is shown below.

        .. figure:: images/c++/creating-a-project-3.png
            :align: center

        |

        Hit *Generate Project* to finalize the creation of the project. There will be a prompt as shown to open in a new window or the current window. A new window will open another instance of VS Code whereas the current window will close the any open project you have and place this project in the currently opened VS Code window.

        .. figure:: images/c++/creating-a-project-4.png
            :align: center

        |

        .. note:: The project will then automatically build for the first time. If the build is not successful, either VS Code and WPILib was installed incorrectly or you are not connected to the internet.

        The VS Code window should now look like this and a Java project has been created!

        .. figure:: images/c++/creating-a-project-5.png
            :align: center
            
        |

        .. important:: After creating a project it is always a good idea to run the ``Change the deploy target to VMX-Pi (from RoboRIO)`` command from the VMX-Pi WPILib extension.   