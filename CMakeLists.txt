project(game.libretro.snes9x-next)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(Kodi REQUIRED)
find_package(libretro-snes9x-next REQUIRED)

set(DEPLIBS snes9x-next)
set(SNES9X-NEXT_CUSTOM_BINARY ${SNES9X-NEXT_LIB}
                              ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX} snes9x-next)

build_addon(${PROJECT_NAME} SNES9X-NEXT DEPLIBS)

