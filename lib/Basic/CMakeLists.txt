add_llbuild_library(llbuildBasic STATIC
  ExecutionQueue.cpp
  FileInfo.cpp
  FileSystem.cpp
  Hashing.cpp
  LaneBasedExecutionQueue.cpp
  PlatformUtility.cpp
  SerialQueue.cpp
  Subprocess.cpp
  Tracing.cpp
  Version.cpp
  ShellUtility.cpp
  )

target_link_libraries(llbuildBasic PRIVATE llvmSupport)

if(${CMAKE_SYSTEM_NAME} MATCHES ".*BSD" OR ${CMAKE_SYSTEM_NAME} MATCHES "Linux")
  target_link_libraries(llbuildBasic pthread)
endif()

if (${CMAKE_SYSTEM_NAME} STREQUAL "Windows")
  target_link_libraries(llbuildBasic ShlWapi.lib)
endif()
