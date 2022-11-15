```cpp
#include "vex.h"

using namespace vex;
using signature = vision::signature;
using code = vision::code;

// A global instance of brain used for printing to the V5 Brain screen
brain  Brain;

// VEXcode device constructors
line RIGHT = line(Brain.ThreeWirePort.E);
motor LeftMotor = motor(PORT2, ratio18_1, false);
motor RightMotor = motor(PORT3, ratio18_1, true);
line CENTER = line(Brain.ThreeWirePort.F);
line LEFT = line(Brain.ThreeWirePort.G);
bumper BumperA = bumper(Brain.ThreeWirePort.A);

// VEXcode generated functions



/**
 * Used to initialize code/tasks/devices added using tools in VEXcode Pro.
 * 
 * This should be called at the start of your int main function.
 */
void vexcodeInit( void ) {
  // nothing to initialize
}
```
