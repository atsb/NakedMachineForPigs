cmake_minimum_required (VERSION 3.25)
project(Launcher)

include_directories(
    ${HPL2_INCLUDE_DIR}
    ${DEP_INCLUDE_DIR}
)

link_directories(
    ${DEP_LIB_DIR}
)

add_executable(Launcher launcher.cpp Main.cpp QualityChooser.cpp LauncherHelper.cpp)
target_link_libraries(Launcher HPL2 fltk_images Xinerama Xfixes Xcursor Xrender fltk Xext X11 Xft fontconfig jpeg)

install(TARGETS Launcher
    RUNTIME DESTINATION "${CMAKE_CURRENT_SOURCE_DIR}/../../redist"
    CONFIGURATIONS Debug)

install(TARGETS Launcher
    RUNTIME DESTINATION "${CMAKE_CURRENT_SOURCE_DIR}/../../Production"
    CONFIGURATIONS RelWithDebInfo)
