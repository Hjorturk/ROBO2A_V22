```` C++
// Hér er tillaga sem ég mæli með að þú prófir:
// ef hann er að beygja illa þá prófa Giro sem þú færð frá mér
#include "vex.h"

using namespace vex;
int turn_list[14]={90,-90,-90,90,90,-90,90,90,-90,90,90,-90,-90,90};
int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  int distance = 500;
  vexcodeInit();
  Drivetrain.setDriveVelocity(25,percent);
  Drivetrain.setTurnVelocity(25,percent);
  for(int i=0;i<=14;i++){
    Drivetrain.driveFor(forward, distance, mm);
    Drivetrain.turnFor(turn_list[i], degrees);
    }
  Drivetrain.driveFor(forward, distance, mm);
}
```
