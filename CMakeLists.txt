cmake_minimum_required(VERSION 3.5)

project(ekosdebugger LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 COMPONENTS Core Core5Compat Widgets Sql Xml DBus REQUIRED)

set(SOURCES
    main.cpp
    debuggerview.cpp
    debuggerview.ui
    userdb.cpp
    profileinfo.cpp
    handler.cpp
    xmldriverslistreader.cpp)

qt6_add_resources(SOURCES resources/resources.qrc)

add_executable(ekosdebugger ${SOURCES})

target_link_libraries(ekosdebugger PRIVATE
    Qt6::Widgets
    Qt6::Sql
    Qt6::Xml
    Qt6::DBus
    Qt6::Core5Compat
    Qt6::Core
    )

install(TARGETS ekosdebugger RUNTIME DESTINATION bin )

