# CMakeList.txt : CMake project for glTF 3D Model Viewer, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.25.1)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("glTF_3DModelViewer")

add_subdirectory(external)
add_subdirectory(src)

if(MSVC)
#Make sure the compiler uses the latest C++ standard.
  target_compile_options("glTF_3DModelViewer" PUBLIC "/Zc:__cplusplus")
endif()

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET "glTF_3DModelViewer" PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
