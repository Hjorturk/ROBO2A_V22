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
// Drivetrain           drivetrain    1, 10, D
// ---- END VEXCODE CONFIGURED DEVICES ----

#include "vex.h"

using namespace vex;

int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  //int distance = 500;
  vexcodeInit();
  /*while (distance <= 2500) {
      Drivetrain.driveFor(forward, distance, mm);
      Drivetrain.driveFor(reverse, distance, mm);
      distance = distance + 500;
  }*/
  for ( int distance = 500; distance < 3000; distance = distance + 500)
    {
      Drivetrain.driveFor(forward, distance, mm);
      Drivetrain.driveFor(reverse, distance, mm);
    }
}
```
