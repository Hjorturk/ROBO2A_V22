``` cpp
#include "vex.h"

using namespace vex;

// Declare Contoller event callbacks.
void whenControllerAPressed() {
    int distance = 500;
    Drivetrain.setDriveVelocity(25,percent);
    Drivetrain.setTurnVelocity(25,percent);
    for(int i=0;i<=14;i++){
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(turn_list[i], degrees);
    }
  Drivetrain.driveFor(forward, distance, mm);
}
int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  vexcodeInit();
  // Initialize the Contoller Events
  Controller1.ButtonA.pressed(whenControllerAPressed);
  Drivetrain.setStopping(brakeType::hold);

  while(true){
      if (Controller1.ButtonX.pressing() || BumperA.pressing()){

   Drivetrain.stop();
      }
    wait(25, msec);
  }
}
```
