cmake_minimum_required(VERSION 3.5)

project(macaroon_msgs)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(msg_files
  "msg/Macaroon.msg"
  "msg/TofuRequest.msg"
  "msg/TofuResponse.msg"
  "msg/AuthenticationRequest.msg"
  "msg/DischargeMacaroon.msg"
  "msg/ResourceTokenRequest.msg"
  "msg/ResourceMacaroon.msg"
  "msg/CommandMacaroon.msg"
)
set(srv_files
  "srv/InitiateTofu.srv"
  "srv/Authenticate.srv"
  "srv/GetResourceToken.srv"
  "srv/UseResourceToken.srv"
)
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files} ${srv_files}
  DEPENDENCIES std_msgs
  ADD_LINTER_TESTS
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
