#cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

#project(trtlab)

#include(GNUInstallDirs)

#option(ENABLE_TESTING "Build tests" ON)

#set(CMAKE_CXX_STANDARD 17)
#set(CMAKE_CXX_EXTENSIONS ON)

#set(CMAKE_DEBUG_POSTFIX "-d")
set(CMAKE_POSITION_INDEPENDENT_CODE TRUE)
#set(default_build_type "Release")

#set(CMAKE_THREAD_PREFER_PTHREAD TRUE)
#find_package(Threads)

#if(ENABLE_TESTING)
#  message(STATUS "Building Tests")
#  find_package(GTest) #1.8.1 CONFIG REQUIRED)
#  find_package(benchmark)
#  enable_testing()
#endif()

# suppress warnings

#add_compile_options(
#  $<$<AND:$<STREQUAL:$<COMPILE_LANGUAGE>,CXX>,$<CXX_COMPILER_ID:AppleClang>>:-Wno-deprecated-declarations>
#)

if(BUILD_MEMORY)
  add_subdirectory(memory)
endif()

if(BUILD_CORE)
  add_subdirectory(core)
endif()

if(BUILD_CUDA)
  add_subdirectory(cuda)
endif()

if(BUILD_NVRPC)
  add_subdirectory(nvrpc)
endif()

if(BUILD_TENSORRT)
   add_subdirectory(tensorrt)
endif()

if(BUILD_PYTHON)
  add_subdirectory(pybind)
endif()


# install

# include(CMakePackageConfigHelpers)
#
# install(
#   EXPORT ${PROJECT_NAME}-targets
#   NAMESPACE ${PROJECT_NAME}::
#   FILE ${PROJECT_NAME}-targets.cmake
#   DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}"
# )
#
# configure_package_config_file(
#   "${CMAKE_CURRENT_SOURCE_DIR}/cmake/${PROJECT_NAME}-config.cmake.in"
#   ${PROJECT_NAME}-config.cmake
#   INSTALL_DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}"
#   NO_CHECK_REQUIRED_COMPONENTS_MACRO
#   PATH_VARS CMAKE_INSTALL_INCLUDEDIR
# )
#
# install(
# # FILES "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}-config.cmake"
#   DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}"
# )
