project(game.libretro.snes9x-next)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(kodi REQUIRED)

include(ExternalProject)
externalproject_add(snes9x-next
                    GIT_REPOSITORY https://github.com/libretro/snes9x-next
                    GIT_TAG 1228cb2
                    PREFIX snes9x-next
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make -f Makefile.libretro
                    BUILD_IN_SOURCE 1)

set(SNES9X-NEXT_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/snes9x-next/src/snes9x-next/snes9x_next_libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                              game.libretro.snes9x-next${CMAKE_SHARED_LIBRARY_SUFFIX} snes9x-next)

build_addon(game.libretro.snes9x-next SNES9X-NEXT DEPLIBS)
add_dependencies(game.libretro.snes9x-next snes9x-next)

include(CPack)
