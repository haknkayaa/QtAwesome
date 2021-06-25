cmake_minimum_required(VERSION 3.9)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

project(QtAwesome VERSION 4.7.1)

set(HEADER_FILES
        include/QtAwesome.h
        include/QtAwesomeAnim.h)

set(SOURCE_FILES
        src/QtAwesome.cpp
        src/QtAwesomeAnim.cpp)

set(RESOURCE_FILES
        resources/QtAwesome.qrc)


find_package(Qt5 REQUIRED Core Gui Widgets)

add_library(QtAwesome STATIC ${HEADER_FILES} ${SOURCE_FILES} ${RESOURCE_FILES})

set_target_properties(QtAwesome PROPERTIES VERSION ${PROJECT_VERSION})
set_target_properties(QtAwesome PROPERTIES PUBLIC_HEADER include/QtAwesome.h)

target_include_directories(QtAwesome PRIVATE include)
target_include_directories(QtAwesome PRIVATE src)

target_link_libraries(QtAwesome Qt5::Core Qt5::Gui Qt5::Widgets)

install(TARGETS QtAwesome
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})