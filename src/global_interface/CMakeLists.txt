cmake_minimum_required(VERSION 3.8)
project(global_interface)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Point2f.msg"
  "msg/Serial.msg"
  "msg/Buff.msg"
  "msg/Armor.msg"
  "msg/Autoaim.msg"
  "msg/Gimbal.msg"
  "msg/Sentry.msg"
  "msg/ObjHP.msg"
  "msg/CarPos.msg"
  "msg/GameInfo.msg"
  "msg/SpinInfo.msg"
  "msg/Detection.msg"
  "msg/DetectionArray.msg"
  "msg/Decision.msg"
  # "srv/*.srv"
  # "action/*.action"
  DEPENDENCIES
  builtin_interfaces
  std_msgs
  geometry_msgs
  sensor_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  
  # msg消息 是ROS topic通讯节点间传递的内容。
  #std消息属于基本数据类型消息，和python类似，描述的是数字，字符串，布尔类型等, geometry空间数据描述, sensor传感器消息
  #.msg文件就是自定义的消息文件，用来描述消息格式
  

  ament_lint_auto_find_test_dependencies()
endif()
  
ament_export_dependencies(rosidl_default_runtime)
ament_package()
