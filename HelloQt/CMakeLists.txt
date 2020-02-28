cmake_minimum_required(VERSION 3.10.0 FATAL_ERROR)

project(HelloQt LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_COLOR_MAKEFILE OFF)
configure_file(main.cpp main.cpp.txt @ONLY)


find_package(Qt5 REQUIRED network serialport)
if ( NOT Qt_FOUND OR NOT QtXml_FOUND )
    endif()


message(-----------**************----------------)
message(${CMAKE_INCLUDE_CURRENT_DIR})

find_package(Qt5 REQUIRED COMPONENTS Core Widgets Gui)

set(project_ui
    mainwindow.ui)

set(project_headers
    mainwindow.h)

set(project_sources
    main.cpp
    mainwindow.cpp)

qt5_wrap_ui(project_headers_wrapped ${project_ui})
qt5_wrap_cpp(project_sources_moc ${project_headers})

add_executable(${PROJECT_NAME} ${project_headers} ${project_sources}
    ${project_sources_moc} ${project_headers_wrapped})

target_link_libraries(${PROJECT_NAME}
    PUBLIC
    Qt5::Core
    Qt5::Gui
    Qt5::Widgets
    Qt5::Network)
