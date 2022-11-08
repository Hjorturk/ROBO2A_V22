``` cpp
#include "vex.h"

using namespace vex;

  const int CENTER_FOV =158;
  const int OFFSET_X = 45;
int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  vexcodeInit();



  vexcodeInit();
  
  while (!Controller1.ButtonA.pressing()) {
    if (!BumperA.pressing()) {
      if (LightB.brightness() >= 50) {
        Brain.Screen.clearLine();
        Vision6.takeSnapshot(Vision6__GREENBOX);
        if (Controller1.ButtonX.pressing() || BumperA.pressing()){
              Drivetrain.stop();
              } else if(Vision6.largestObject.exists){
          Brain.Screen.print(Vision6.largestObject.width);
          if(Vision6.largestObject.width < 90){
            Drivetrain.drive(forward);
          } else if(Vision6.largestObject.width >= 100){
            Drivetrain.drive(reverse);
          } else if(Vision6.largestObject.centerX > CENTER_FOV + OFFSET_X){
            Drivetrain.turn(right);
          }
          else if (Vision6.largestObject.centerX < CENTER_FOV - OFFSET_X) {
            Drivetrain.turn(left);
          }
          else{
            Drivetrain.stop(brakeType::brake);
          }
  }
  
  } else {
    Drivetrain.stop();
  }
} else {
  Drivetrain.stop();
}
  }
}
```
