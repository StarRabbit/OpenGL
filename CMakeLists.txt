cmake_minimum_required(VERSION 3.12)
project(OpenGL)

set(CMAKE_CXX_STANDARD 14)

set(GLEW_H /usr/local/Cellar/glew/2.1.0_1/include/GL)
set(GLFW_H /usr/local/Cellar/glfw/3.3.1/include/GLFW)
set(GLAD_H /usr/local/include/glad)
set(KH_H /usr/local/include/KHR)
include_directories(${GLEW_H} ${GLFW_H} ${GLAD_H} ${KH_H})

# 添加目标链接
set(GLEW_LINK /usr/local/Cellar/glew/2.1.0_1/lib/libGLEW.2.1.dylib)
set(GLFW_LINK /usr/local/Cellar/glfw/3.3.1/lib/libglfw.3.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

# 执行编译命令
# 这个glad.c在第2步中说过要拉到项目中，注意路径
set(SOURCE_FILES "src/glad.c" "control.cpp" "createpacman.cpp" "food.cpp" "gameover.cpp" "gameresult.cpp" "gamestart.cpp" "init.cpp" "laberynth.cpp" "monster.cpp" "Pacman.cpp")
add_executable(OpenGL ${SOURCE_FILES})

# mac下这步很重要
if (APPLE)
    target_link_libraries(OpenGL "-framework OpenGL")
    target_link_libraries(OpenGL "-framework GLUT")
endif()