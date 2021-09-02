# quori_arms_embedded

## Installation

Unfortunately the arduino IDE doesn't support preprocessor arguments on the command line. We must modify the source code directly for each microcontroller.

### Left Arm
  1. Disconnect all microcontrollers (arms and spine) from the computer.
  2. Plug in the left arm
  3. Open `arm/arm.ino` in the arduino IDE
  4. At the top of the file, configure the `QUORI_CONFIG_ZERO_POSITION_X` and `QUORI_CONFIG_ZERO_POSITION_Y`. Ensure `QUORI_CONFIG_ARM_LEFT` is **uncommented** and `QUORI_CONFIG_ARM_RIGHT` is **commented**.
  5. Upload to the left arm's microcontroller
  6. Unplug the left arm

### Right Arm
  1. Disconnect all microcontrollers (arms and spine) from the computer.
  2. Plug in the right arm
  3. Open `arm/arm.ino` in the arduino IDE
  4. At the top of the file, configure the `QUORI_CONFIG_ZERO_POSITION_X` and `QUORI_CONFIG_ZERO_POSITION_Y`. Ensure `QUORI_CONFIG_ARM_LEFT` is **commented** and `QUORI_CONFIG_ARM_RIGHT` is **uncommented**.
  5. Upload to the right arm's microcontroller
  6. Unplug the right arm

### Spine
  1. Disconnect all microcontrollers (arms and spine) from the computer.
  2. Plug in the spine
  3. Open `spine/spine.ino` in the arduino IDE
  4. At the top of the file, configure the `QUORI_CONFIG_ZERO_POSITION_WAIST` and `QUORI_CONFIG_ZERO_POSITION_MOTOR`.
  5. Upload to the spine's microcontroller
  6. Unplug the spine

### `udev` Rules
  1. Connect all microcontrollers
  2. Run `sudo /opt/quori/devel/lib/quori_controller/init`
  3. Reboot

To verify success, `ls -l /dev/quori` should list the `left_arm`, `right_arm`, `waist`, and `base`.

## Testing

```sh
# Source quori's ROS packages
. /opt/quori/setup.bash

# Launch ros_control
roslaunch quori_controller quori_control_holo.launch

# Launch rqt_joint_trajectory_controller
/opt/ros/noetic/lib/rqt_joint_trajectory_controller/rqt_joint_trajectory_controller
```

Select the quori_controller in the GUI. You should then be able to move the joints.