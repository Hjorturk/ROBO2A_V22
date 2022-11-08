``` cpp
#include "vex.h"

using namespace vex;

event checkRed = event();
event checkBlue = event();
event checkGreen = event();

void hasBlueCallback() {
  Brain.Screen.setFont(mono40);
  Brain.Screen.clearLine(1, black);
  Brain.Screen.setCursor(Brain.Screen.row(), 1);
  Brain.Screen.setCursor(1, 1);
  Vision6.takeSnapshot(Vision6__BLUEBOX);
  if (Vision6.objectCount > 0) {
    Brain.Screen.print("Þetta er fjólublátt");
  } else {
    Brain.Screen.print("Ekkert Fjólublátt");
  }
}

void hasRedCallback() {
  Brain.Screen.setFont(mono40);
  Brain.Screen.clearLine(3, black);
  Brain.Screen.setCursor(Brain.Screen.row(), 1);
  Brain.Screen.setCursor(3, 1);
  Vision6.takeSnapshot(Vision6__REDBOX);
  if (Vision6.objectCount > 0) {
    Brain.Screen.print("Appelsínugulur hlutur í mynd");
  } else {
    Brain.Screen.print("Ekkert appelsínugult");
  }
}

void hasGreenCallback() {
  Brain.Screen.setFont(mono40);
  Brain.Screen.clearLine(5, black);
  Brain.Screen.setCursor(Brain.Screen.row(), 1);
  Brain.Screen.setCursor(5, 1);
  Vision6.takeSnapshot(Vision6__GREENBOX);
  if (Vision6.objectCount > 0) {
    Brain.Screen.print("Grænn hlutur í mynd");
  } else {
    Brain.Screen.print("Ekkert grænt");
  }
}

int main() {
  // Initializing Robot Configuration. DO NOT REMOVE!
  vexcodeInit();

  checkBlue(hasBlueCallback);
  checkRed(hasRedCallback);
  checkGreen(hasGreenCallback);
  
  while (true) {
    checkBlue.broadcastAndWait();
    checkRed.broadcastAndWait();
    checkGreen.broadcastAndWait();
    wait(1, seconds);
  }
}
```
