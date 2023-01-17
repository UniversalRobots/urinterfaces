cmake_minimum_required(VERSION 3.5)

project(ur_interfaces)

# Default to C++17
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(action_msgs REQUIRED)

set(msg_files
  "msg/Analog.msg"
  "msg/BoolStamped.msg"
  "msg/ControlCycle.msg"
  "msg/Current.msg"
  "msg/DigitalPort.msg"
  "msg/DoubleMultiArrayStamped.msg"
  "msg/Float32Stamped.msg"
  "msg/Float64Stamped.msg"
  "msg/JointMode.msg"
  "msg/JointTemperature.msg"
  "msg/JointVoltage.msg"
  "msg/RobotMode.msg"
  "msg/RuntimeState.msg"
  "msg/SafetyStatus.msg"
  "msg/SpeedSliderFraction.msg"
  "msg/TCPState.msg"
  "msg/ProgramState.msg"
  "msg/ToolOutputMode.msg"
  "msg/VoltageCurrentStamped.msg"
  "msg/WorldModelNames.msg"
)

set(srv_files
  "srv/SetAnalogOutput.srv"
  "srv/SetDigitalOutput.srv"
  "srv/SetSpeedFraction.srv"
  "srv/AddToLog.srv"
  "srv/GetLoadedProgram.srv"
  "srv/GetProgramState.srv"
  "srv/GetRobotMode.srv"
  "srv/SetPayload.srv"
  "srv/GetSafetyMode.srv"
  "srv/IsProgramRunning.srv"
  "srv/IsProgramSaved.srv"
  "srv/Load.srv"
  "srv/Popup.srv"
  "srv/RawRequest.srv"
)

set(action_files
  "action/SetMode.action"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  ${action_files}
  DEPENDENCIES builtin_interfaces std_msgs geometry_msgs sensor_msgs action_msgs
  ADD_LINTER_TESTS
)

ament_export_dependencies(rosidl_default_runtime)
ament_package()
