``` cpp
#include "vex.h"

using namespace vex;
using signature = vision::signature;
using code = vision::code;

// A global instance of brain used for printing to the V5 Brain screen
brain  Brain;

// VEXcode device constructors
motor LeftDriveSmart = motor(PORT2, ratio18_1, false);
motor RightDriveSmart = motor(PORT3, ratio18_1, true);
drivetrain Drivetrain = drivetrain(LeftDriveSmart, RightDriveSmart, 319.19, 295, 40, mm, 1);
motor ClawMotor = motor(PORT4, ratio18_1, false);
motor ArmMotor = motor(PORT5, ratio18_1, false);
controller Controller1 = controller(primary);
bumper BumperA = bumper(Brain.ThreeWirePort.A);
light LightB = light(Brain.ThreeWirePort.B);
sonar RangeFinderC = sonar(Brain.ThreeWirePort.C);
/*vex-vision-config:begin*/
signature Vision6__GREENBOX = signature (1, -7373, -5389, -6382, -4097, -2765, -3432, 3, 0);
signature Vision6__SIG_2 = signature (2, 0, 0, 0, 0, 0, 0, 3, 0);
signature Vision6__SIG_3 = signature (3, 0, 0, 0, 0, 0, 0, 3, 0);
signature Vision6__SIG_4 = signature (4, 0, 0, 0, 0, 0, 0, 3, 0);
signature Vision6__SIG_5 = signature (5, 0, 0, 0, 0, 0, 0, 3, 0);
signature Vision6__SIG_6 = signature (6, 0, 0, 0, 0, 0, 0, 3, 0);
signature Vision6__SIG_7 = signature (7, 0, 0, 0, 0, 0, 0, 3, 0);
vision Vision6 = vision (PORT6, 50, Vision6__GREENBOX, Vision6__SIG_2, Vision6__SIG_3, Vision6__SIG_4, Vision6__SIG_5, Vision6__SIG_6, Vision6__SIG_7);
/*vex-vision-config:end*/

// VEXcode generated functions
// define variable for remote controller enable/disable
bool RemoteControlCodeEnabled = true;
// define variables used for controlling motors based on controller inputs
bool Controller1LeftShoulderControlMotorsStopped = true;
bool Controller1RightShoulderControlMotorsStopped = true;
bool DrivetrainNeedsToBeStopped_Controller1 = true;

// define a task that will handle monitoring inputs from Controller1
int rc_auto_loop_function_Controller1() {
  // process the controller input every 20 milliseconds
  // update the motors based on the input values
  while(true) {
    if(RemoteControlCodeEnabled) {
      // calculate the drivetrain motor velocities from the controller joystick axies
      // left = Axis2 + Axis1
      // right = Axis2 - Axis1
      int drivetrainLeftSideSpeed = Controller1.Axis2.position() + Controller1.Axis1.position();
      int drivetrainRightSideSpeed = Controller1.Axis2.position() - Controller1.Axis1.position();
      
      // check if the values are inside of the deadband range
      if (abs(drivetrainLeftSideSpeed) < 5 && abs(drivetrainRightSideSpeed) < 5) {
        // check if the motors have already been stopped
        if (DrivetrainNeedsToBeStopped_Controller1) {
          // stop the drive motors
          LeftDriveSmart.stop();
          RightDriveSmart.stop();
          // tell the code that the motors have been stopped
          DrivetrainNeedsToBeStopped_Controller1 = false;
        }
      } else {
        // reset the toggle so that the deadband code knows to stop the motors next time the input is in the deadband range
        DrivetrainNeedsToBeStopped_Controller1 = true;
      }
      
      // only tell the left drive motor to spin if the values are not in the deadband range
      if (DrivetrainNeedsToBeStopped_Controller1) {
        LeftDriveSmart.setVelocity(drivetrainLeftSideSpeed, percent);
        LeftDriveSmart.spin(forward);
      }
      // only tell the right drive motor to spin if the values are not in the deadband range
      if (DrivetrainNeedsToBeStopped_Controller1) {
        RightDriveSmart.setVelocity(drivetrainRightSideSpeed, percent);
        RightDriveSmart.spin(forward);
      }
      // check the ButtonL1/ButtonL2 status to control ClawMotor
      if (Controller1.ButtonL1.pressing()) {
        ClawMotor.spin(forward);
        Controller1LeftShoulderControlMotorsStopped = false;
      } else if (Controller1.ButtonL2.pressing()) {
        ClawMotor.spin(reverse);
        Controller1LeftShoulderControlMotorsStopped = false;
      } else if (!Controller1LeftShoulderControlMotorsStopped) {
        ClawMotor.stop();
        // set the toggle so that we don't constantly tell the motor to stop when the buttons are released
        Controller1LeftShoulderControlMotorsStopped = true;
      }
      // check the ButtonR1/ButtonR2 status to control ArmMotor
      if (Controller1.ButtonR1.pressing()) {
        ArmMotor.spin(forward);
        Controller1RightShoulderControlMotorsStopped = false;
      } else if (Controller1.ButtonR2.pressing()) {
        ArmMotor.spin(reverse);
        Controller1RightShoulderControlMotorsStopped = false;
      } else if (!Controller1RightShoulderControlMotorsStopped) {
        ArmMotor.stop();
        // set the toggle so that we don't constantly tell the motor to stop when the buttons are released
        Controller1RightShoulderControlMotorsStopped = true;
      }
    }
    // wait before repeating the process
    wait(20, msec);
  }
  return 0;
}

/**
 * Used to initialize code/tasks/devices added using tools in VEXcode Pro.
 * 
 * This should be called at the start of your int main function.
 */
void vexcodeInit( void ) {
  task rc_auto_loop_task_Controller1(rc_auto_loop_function_Controller1);
}
```
