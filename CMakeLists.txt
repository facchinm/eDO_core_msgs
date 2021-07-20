cmake_minimum_required(VERSION 3.5)

project(edo_core_msgs)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(std_msgs REQUIRED)

## Generate messages in the 'msg' folder
set(msg_files
  msg/CartesianPose.msg
  msg/EdoError.msg
  msg/Frame.msg
  msg/JointCalibration.msg
  msg/JointConfigurationArray.msg
  msg/JointConfiguration.msg
  msg/JointControlArray.msg
  msg/JointControl.msg
  msg/JointFwVersionArray.msg
  msg/JointFwVersion.msg
  msg/JointInit.msg
  msg/JointMonitoring.msg
  msg/JointReset.msg
  msg/JointsPositions.msg
  msg/JointStateArray.msg
  msg/JointState.msg
  msg/MachineState.msg
  msg/MovementCommand.msg
  msg/MovementFeedback.msg
  msg/NodeSwVersionArray.msg
  msg/NodeSwVersion.msg
  msg/Point.msg
  msg/SystemCommand.msg
)

## Generate services in the 'srv' folder

set(srv_files
  srv/ControlSwitch.srv
  srv/DirectKinematics.srv
  srv/InverseKinematics.srv
  srv/JointsNumber.srv
  srv/LoadConfigurationFile.srv
  srv/SoftwareVersion.srv
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES builtin_interfaces geometry_msgs std_msgs
  ADD_LINTER_TESTS
)
ament_export_dependencies(rosidl_default_runtime)
ament_package()
