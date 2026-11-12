# 3-DoF Robotic Arm for a Soft Granular Jamming Gripper

A lightweight 3D-printed robotic arm designed to carry a soft gripper for automated strawberry packaging. BEng final project at Queen Mary University of London (Grade: 86%).


## The problem

Strawberries are packed largely by hand. That's slow, costly, causes bruising that shortens shelf life, and puts workers at risk of repetitive strain injury. A soft granular jamming gripper can handle fruit gently, but it needs an arm to move it. Building that arm was my part of a multidisciplinary team project.

## Design

**Sizing from the motors.** Only two DYNAMIXEL XC430-W240 servos were available. Using 80% of the stall torque as a safe limit (1.52 Nm), I calculated a maximum supportable weight of 0.775 kg at a 200 mm lever arm. That set the link lengths at 200 mm and 100 mm. The base and elbow joints are motorised, and the shoulder is manually adjustable, keeping three degrees of freedom.

**Choosing the link shape.** I wrote MATLAB code comparing the section modulus (bending resistance) of solid cylindrical beams with parallel rectangular beams across a range of cross-sectional areas. The parallel beams were stiffer at every size, so they replaced the original wooden-dowel concept.

**Two prototypes.** I modelled the arm in SolidWorks and 3D printed it in PLA.
- The first prototype (70% infill) couldn't be assembled: misaligned holes, a motor mount that didn't hold the motor, and no allowance for the motor's raised face.
- I redesigned the base, brackets, link connector and motor interfaces, and cut infill to 40%. The final arm weighs **0.35 kg** and assembled cleanly. It also includes a mount for a Raspberry Pi camera to support future object detection.

## Testing

The arm was driven from a PC through a U2D2 interface.

| Test | Result |
|---|---|
| Workspace | 110–255 mm reach, 295° rotation |
| Repeatability (20 runs to the same point) | **3.95 mm mean error**, 1.99 mm standard deviation |
| Load | Reliably lifted the 70 g gripper. Positioning error grew by about 0.155 mm per gram added |

**What the results showed:**
- The reach fell short of the predicted 300 mm because the links overlap at the joints. Slightly longer links would fix this.
- The missing 65° of rotation came from software motor limits, not hardware.
- Above 80 g, the end of the arm began to sag, which points to PLA's limited stiffness.

## Next steps

- Cast the final version in aluminium using the lost-PLA method, for a better strength-to-weight ratio and durability
- Improve the control system to unlock full rotation and compensate for load
- Add proximity sensing for safety around workers

## Repository contents
- Design report PDF
- Photos / video of the arm

## Tech stack

SolidWorks · MATLAB · 3D printing (PLA) · DYNAMIXEL servos · U2D2

---
Kimberly Nweze · [Portfolio](https://kimberlysonweze.github.io/kimberlynweze.github.io/) · BEng Robotic Engineering, Queen Mary University of London
