cmake_minimum_required(VERSION 3.8)
project(bupt_rc_cv_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

# 添加自定义消息类型
find_package(rosidl_default_generators REQUIRED)
rosidl_generate_interfaces(${PROJECT_NAME}  
    "msg/CVCamera.msg"                      # Camera的msg
    "msg/CVCameraArray.msg"                 # Camera的msg数组
    "msg/CVInference.msg"                   # Inference的基本msg
    "msg/CVInferenceResult.msg"             # 一个摄像头推理的结果
    "msg/CVInferenceArray.msg"              # 多个摄像头推理的结果
    "msg/CVFrame.msg"                       # 图片数据的msg
    "srv/CVDepth.srv"                       # 深度数据的Srv
    "srv/CVInferenceSendImg.srv"            # 控制推理是否发送图片数据
    "srv/CVInferenceSwitch.srv"             # 控制是否进行推理
)

ament_package()
