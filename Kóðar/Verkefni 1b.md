``` cpp
/*----------------------------------------------------------------------------*/
/*                                                                            */
/*    Module:       main.cpp                                                  */
/*    Author:       VEX                                                       */
/*    Created:      Wed Sep 25 2019                                           */
/*    Description:  Moving Forward (mm)                                       */
/*                                                                            */
/*    This Program drives the robot forward for 150 millimeters.              */
/*                                                                            */
/*                                                                            */
/*----------------------------------------------------------------------------*/

// ---- START VEXCODE CONFIGURED DEVICES ----
// Robot Configuration:
// [Name]               [Type]        [Port(s)]
// Drivetrain           drivetrain    1, 10           
// ---- END VEXCODE CONFIGURED DEVICES ----

#include "vex.h"

using namespace vex;

int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  int distance = 500;
  vexcodeInit();
    Drivetrain.setDriveVelocity(25,percent);
    Drivetrain.setTurnVelocity(25,percent);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(-90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(-90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(80, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(-90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(-90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(80, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(-90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(-90, degrees);
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(90, degrees);
    Drivetrain.driveFor(forward, distance+100, mm);
}
```
