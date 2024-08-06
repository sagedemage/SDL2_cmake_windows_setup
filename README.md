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

## 3. Build the Program
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
