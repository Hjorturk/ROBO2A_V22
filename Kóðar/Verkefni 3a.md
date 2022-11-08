``` cpp
#include "vex.h"

using namespace vex;

int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  vexcodeInit();
  while (!Controller1.ButtonA.pressing()) {
    if (!BumperA.pressing()) {
      if (LightB.brightness() >= 50) {
        if (RangeFinderC.distance(mm) >= 350) {
          Drivetrain.drive(forward);
          if (Controller1.ButtonX.pressing() || BumperA.pressing()){
              Drivetrain.stop();
              } 

        } else if (RangeFinderC.distance(mm) < 350) {
          Drivetrain.driveFor(reverse, 50, mm);
          Drivetrain.turnFor(right, 90, degrees);
        }
      } else if (LightB.brightness() < 50) {
        Drivetrain.stop();
      }
    } else if (BumperA.pressing()){
      Drivetrain.stop();
    }
  }
}

```
