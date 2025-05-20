# Exodapt AI Robot Interfaces

This repository contains custom ROS 2 interface definitions (messages, services, actions) used in the development of Exodapt AI powered robots.

## Contents

* `msg/`: Custom message definitions.
* `srv/`: Custom service definitions.
* `action/`: Custom action definitions.

## Provided Interfaces

### Services (`srv/`)

* `State.srv` - Service to query the robot's state.

### Actions (`action/`)

* `ActionDecision.action` - Action for predicting next action to take
* `ActionReply.action` - Action for generating a reply based on the current state and instruction
* `LLM.action` - Action for generating a response from a Large Language Model (LLM).

## Usage

This repository should be included as a dependency in the robot's ROS 2 workspace.

1. Add this repository into your repository's .rosinstall file (in repository root directory):
    ```
    repositories:
      exodapt_robot_interfaces:
        type: git
        url: https://github.com/robin-karlsson0/exodapt_robot_interfaces.git
        version: main
        path: ros2_ws/src/exodapt_robot_interfaces
    ```

2. Import this repository into your ROS 2 workspace's `src/` directory:
   ```sh
   vcs import ros2_ws/src/ < .rosinstall
   ```

3. Build the workspace using colcon:
   ```sh
   colcon build
   ```

4. In your package's `package.xml`, add the dependency:
   ```xml
   <depend>exodapt_robot_interfaces</depend>
   ```

4. In your C++ code, include the interfaces:
   ```cpp
   #include "exodapt_robot_interfaces/action/action_decision.hpp"
   #include "exodapt_robot_interfaces/action/action_reply.hpp"
   #include "exodapt_robot_interfaces/action/llm.hpp"
   #include "exodapt_robot_interfaces/srv/state.hpp"
   ```

5. Or in Python:
   ```python
   from exodapt_robot_interfaces.action import ActionDecision, ActionReply, LLM
   from exodapt_robot_interfaces.srv import State
   ```

## License

This project is licensed under the Apache-2.0 License - see the [LICENSE](LICENSE) file for details.

## Notes

This package requires ROS 2 Jazzy (or compatible) and is built using `ament_cmake` and `rosidl_default_generators`.
