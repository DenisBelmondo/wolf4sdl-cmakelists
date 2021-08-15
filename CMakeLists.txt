cmake_minimum_required(VERSION 3.0.0)
project(wolf4sdl VERSION 0.1.0)

include(CTest)
enable_testing()

set(WOLF4SDL_SOURCE_DIR CACHE PATH "")

set(SDL2_INCLUDE_DIR CACHE PATH "")
set(SDL2_MIXER_INCLUDE_DIR CACHE PATH "")
set(SDL2_LIBRARY CACHE FILEPATH "")
set(SDL2MAIN_LIBRARY CACHE FILEPATH "")
set(SDL2_MIXER_LIBRARY CACHE FILEPATH "")

set(LUA_INCLUDE_DIR CACHE PATH "")
set(LUA_LIBRARY CACHE FILEPATH "")

add_executable(wolf4sdl)

target_sources(wolf4sdl PUBLIC
    ${WOLF4SDL_SOURCE_DIR}/dosbox/dbopl.cpp
    ${WOLF4SDL_SOURCE_DIR}/id_ca.cpp
    ${WOLF4SDL_SOURCE_DIR}/id_in.cpp
    ${WOLF4SDL_SOURCE_DIR}/id_pm.cpp
    ${WOLF4SDL_SOURCE_DIR}/id_sd.cpp
    ${WOLF4SDL_SOURCE_DIR}/id_us_1.cpp
    ${WOLF4SDL_SOURCE_DIR}/id_vh.cpp
    ${WOLF4SDL_SOURCE_DIR}/id_vl.cpp
    ${WOLF4SDL_SOURCE_DIR}/signon.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_act1.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_act2.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_agent.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_atmos.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_cloudsky.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_debug.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_draw.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_floorceiling.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_game.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_inter.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_main.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_menu.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_parallax.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_play.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_state.cpp
    ${WOLF4SDL_SOURCE_DIR}/wl_text.cpp
    ${WOLF4SDL_SOURCE_DIR}/states.cpp

    ${WOLF4SDL_SOURCE_DIR}/cc_lua.cpp
)

target_include_directories(wolf4sdl PUBLIC ${SDL2_INCLUDE_DIR})
target_include_directories(wolf4sdl PUBLIC ${SDL2_MIXER_INCLUDE_DIR})
target_include_directories(wolf4sdl PUBLIC ${LUA_INCLUDE_DIR})

target_link_libraries(wolf4sdl ${SDL2_LIBRARY})
target_link_libraries(wolf4sdl ${SDL2MAIN_LIBRARY})
target_link_libraries(wolf4sdl ${SDL2_MIXER_LIBRARY})

target_link_libraries(wolf4sdl ${LUA_LIBRARY})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
