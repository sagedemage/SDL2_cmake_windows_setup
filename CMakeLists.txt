cmake_minimum_required(VERSION 3.24)
# Set the project Name
project(SDLSetup)
# Set the C++ Standard to compile against
set(CMAKE_CXX_STANDARD 11)

# Set Directories for SDL2
set(SDL2_DIR "C:\\vclib\\SDL2-2.30.5\\cmake")
set(SDL2_INCLUDE_DIRS "C:\\vclib\\SDL2-2.30.5\\include")
set(SDL2_LIB_DIR "C:\\vclib\\SDL2-2.30.5\\lib\\x64")

# Set Directories for SDL2_image
set(SDL2_image_DIR "C:\\vclib\\SDL2_image-2.8.2\\cmake")
set(SDL2_IMAGE_INCLUDE_DIR "C:\\vclib\\SDL2_image-2.8.2\\include")

# Set the library path for the SDL2_image.lib file
set(SDL2_IMAGE_LIB "C:\\vclib\\SDL2_image-2.8.2\\lib\\x64\\SDL2_image.lib")

# Set Directories for SDL2_mixer
set(SDL2_mixer_DIR "C:\\vclib\\SDL2_mixer-2.8.0\\cmake")
set(SDL2_MIXER_INCLUDE_DIR "C:\\vclib\\SDL2_mixer-2.8.0\\include")

# Set the library path for the SDL2_mixer.lib file
set(SDL2_MIXER_LIB "C:\\vclib\\SDL2_mixer-2.8.0\\lib\\x64\\SDL2_mixer.lib")

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)
find_package(SDL2_mixer REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_IMAGE_INCLUDE_DIR} ${SDL2_MIXER_INCLUDE_DIR})

file(COPY src/assets DESTINATION ${CMAKE_BINARY_DIR})

add_executable(SDLSetup src/main.cpp)
target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES} ${SDL2_IMAGE_LIB} ${SDL2_MIXER_LIB})