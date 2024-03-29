cmake_minimum_required(VERSION 3.28)

if (POLICY CMP0141)
    cmake_policy(SET CMP0141 NEW)
    set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project(ASSIMPTEST)

include_directories(includes)
include_directories(mesh)
include_directories(libs/assimp/include)

add_subdirectory(libs/glfw-3.4)

#set(BUILD_SHARED_LIBS OFF)
add_subdirectory(libs/assimp)

add_executable(ASSIMPTEST
        main.cpp
        core/glad.c
        core/Vertex.h
        core/Vertex.cpp
        core/Shader.h
        core/Shader.cpp
        core/FileManager.cpp
        core/Camera.cpp
        core/Camera.h
        Mesh/Box.cpp
        Mesh/Box.h
        Mesh/NPC.cpp
        Mesh/NPC.h
        Mesh/Plane.cpp
        Mesh/Plane.h
        core/Mesh/Mesh.cpp
        core/Mesh/Mesh.h
        core/Mesh/Texture.cpp
        core/Mesh/Texture.h
)

target_link_libraries(ASSIMPTEST glfw)
target_link_libraries(ASSIMPTEST assimp)

set(CMAKE_CXX_STANDARD 26)

