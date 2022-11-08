```cpp
#include "vex.h"

using namespace vex;
using signature = vision::signature;
using code = vision::code;

// A global instance of brain used for printing to the V5 Brain screen
brain  Brain;

// VEXcode device constructors
/*vex-vision-config:begin*/
signature Vision6__BLUEBOX = signature (1, -3441, -2785, -3113, 8975, 10355, 9665, 5.3, 0);
signature Vision6__GREENBOX = signature (2, -5767, -4965, -5366, -3803, -2861, -3332, 2.5, 0);
signature Vision6__REDBOX = signature (3, 8099, 8893, 8496, -1505, -949, -1227, 2.5, 0);
signature Vision6__SIG_4 = signature (4, 0, 0, 0, 0, 0, 0, 3, 0);
vision Vision6 = vision (PORT6, 51, Vision6__BLUEBOX, Vision6__GREENBOX, Vision6__REDBOX, Vision6__SIG_4);
/*vex-vision-config:end*/

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
