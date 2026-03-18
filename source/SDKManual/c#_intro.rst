C#
==============

Dieses Dokument ist die Schnittstellenbeschreibung für die sekundäre Entwicklung in der C#-Version.

.. important::

    Erläuterung der Roboterparametereinheiten: Die Roboterpositionseinheit ist Millimeter (mm) und die Ausrichtungseinheit ist Grad (°).

.. important::

    1) Sofern nicht anders angegeben, wird in den Codebeispielen davon ausgegangen, dass der Roboter normal eingeschaltet und aktiviert (Enable) ist.
    2) Es wird in allen Codebeispielen dieses Dokuments davon ausgegangen, dass sich im Arbeitsraum des Roboters keine Hindernisse befinden.
    3) Verwenden Sie für praktische Tests bitte die Daten des vor Ort befindlichen Roboters.
    4) Vor der Verwendung dieses SDKs muss das Paket "xmlrpcnet" über NuGet gesucht und dem Projekt als Referenz hinzugefügt werden.

.. toctree::
    :numbered: 5
    :maxdepth: 5

    C#VersionIntro
    C#DataStructure
    C#RobotBase
    C#RobotMovement
    C#RobotIO
    C#RobotCommonSettings
    C#RobotSecuritySettings
    C#RobotStatusInquiry
    C#RobotTrajectoryRecurrence
    C#RobotWebAPPProgramUse
    C#RobotPeripherals
    C#RobotForceControl
    C#RobotExtendedAxis
    C#RobotWelding
    C#RobotOther
    C#Appendix