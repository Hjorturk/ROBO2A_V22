```cpp
#include "vex.h"

using namespace vex;

float threshold;

int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  vexcodeInit();

  float threshold = 150;
  while (true) {
    Brain.Screen.setCursor(1,1);
    Brain.Screen.print(LEFT.reflectivity());
    Brain.Screen.setCursor(3,1);
    Brain.Screen.print(CENTER.reflectivity());
    Brain.Screen.setCursor(5,1);
    Brain.Screen.print(RIGHT.reflectivity());
      if (CENTER.reflectivity() < threshold) {
        RightMotor.spin(forward);
        LeftMotor.spin(forward);
      } else if (LEFT.reflectivity() < threshold) {
        RightMotor.spin(forward);
        LeftMotor.stop();
      } else if (RIGHT.reflectivity() < threshold) {
        RightMotor.stop();
        LeftMotor.spin(forward);
      } else {
        LeftMotor.stop();
        RightMotor.stop();
      }
      wait(5, msec);
    }
  }
```
