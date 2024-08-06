# SDL2_cmake_window_setup
Setup guide to install SDL2 on Windows with CMake.

## 1. Download the SDL, SDL_mixer, and SDL_image Development Libaries
1. Go to this page to download the lastest SDL and SDL_mixer VC++ development libaries:
    - https://github.com/libsdl-org/SDL/releases
    - https://github.com/libsdl-org/SDL_mixer/releases
    - https://github.com/libsdl-org/SDL_image/releases

2. Download these files (**SDL2-devel-2.30.5-VC.zip**, **SDL2_mixer-devel-2.8.0-VC.zip**, **SDL2_image-devel-2.8.2-VC.zip**)

2. Extract the zip files (**SDL2-devel-2.30.5-VC.zip**, **SDL2_mixer-devel-2.8.0-VC.zip**, **SDL2_image-devel-2.8.2-VC.zip**)

3. Create a folder called `vclib` at C drive (`C:\vclib`).

4. Copy the folders (`SDL2-2.30.5`, `SDL2_mixer-2.8.0`, `SDL2_image-2.8.2`) to `C:\vclib`
    - SDL Folder: `SDL2-devel-2.30.5-VC\SDL2-2.30.5`
    - SDL_mixer Folder: `SDL2_mixer-devel-2.8.0-VC\SDL2_mixer-2.8.0`
    - SDL_image Folder: `SDL2_image-devel-2.8.2-VC\SDL2_image-2.8.2`

## 2. Setup Environmental Variables for SDL, SDL_mixer and SDL_image
1. Go to Settings -> Search and click *Edit the system environment variables* -> Click *Environment Variables*

2. Edit the **Path** under the *System varables*:
```
C:\vclib\SDL2-2.30.5\lib\x64
C:\vclib\SDL2_mixer-2.8.0\lib\x64
C:\vclib\SDL2_image-2.8.2\lib\x64
```

**Note**: to add multiple paths add a semicolon after each path

## 3. Configure the Project with CMake
Copy this configuration to the `CMakeLists.txt` file. The comments explain what portions of the configuration code do what for CMake.
```
cmake_minimum_required(VERSION 3.30)
# Set the project Name
project(SDLSetup)

# Set the C++ Standard to compile against
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set C++ Flags
set(OPTIMIZE_FLAG "-O2")
set(WARNING_FLAGS "-Werror -Wpedantic -Wall -Wextra -Wno-zero-as-null-pointer-constant -Wno-unsafe-buffer-usage")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OPTIMIZE_FLAG} ${WARNING_FLAGS}")

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
```

## 4. Build the Program
1. Setup the CMake build directory
```
.\setup.bat
```

2. Run the program 
```
cd build
.\Debug\SDLSetup.exe
```

## Resources:
- [Setting up SDL 2 on Visual Studio 2019 Community Edition](https://lazyfoo.net/tutorials/SDL/01_hello_SDL/windows/msvc2019/index.php)
