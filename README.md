# ZWidget
A framework for building user interface applications

# ubuntu env
- 1, install SDL2
- ```
  sudo apt install -y libsdl2-dev libsdl2-2.0-0 libsdl2-image-dev libsdl2-ttf-dev libsdl2-mixer-dev
  ```
- 2, change CMakeLists.txt
- ```
  if(ENABLE_SDL2)
  	find_package(SDL2 QUIET)
  	if(NOT ${SDL2_FOUND})
  		include(FindPkgConfig)
  		pkg_search_module(SDL2 sdl2)
          endif()
          if(NOT TARGET SDL2::SDL2)
            add_library(SDL2::SDL2 UNKNOWN IMPORTED)
            set(SDL2_LIBRARIES "/usr/lib/x86_64-linux-gnu/libSDL2.so")
            set(SDL2_INCLUDE_DIRS "/usr/include/SDL2")
            set_target_properties(SDL2::SDL2 PROPERTIES
              IMPORTED_LOCATION "${SDL2_LIBRARIES}"
              INTERFACE_INCLUDE_DIRECTORIES "${SDL2_INCLUDE_DIRS}")
          endif()
  endif()
  ```
