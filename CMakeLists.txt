#
# General
#

cmake_minimum_required(VERSION 2.6)
project(icons)

include_directories(.)

add_definitions(-std=c++11)
file(GLOB icons_SOURCES "*.cpp")
file(GLOB icons_HEADERS "*.h")
file(GLOB icons_FORMS "*.ui")
file(GLOB icons_RESOURCES "*.qrc")

FIND_PACKAGE(Qt4 REQUIRED)
INCLUDE(${QT_USE_FILE})

QT4_WRAP_CPP(icons_HEADERS_MOC ${icons_HEADERS})
QT4_WRAP_UI(icons_FORMS_HEADERS ${icons_FORMS})
QT4_ADD_RESOURCES(icons_RESOURCES_RCC ${icons_RESOURCES})

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR})
ADD_DEFINITIONS(${QT_DEFINITIONS})

ADD_EXECUTABLE(icons_gui ${icons_SOURCES} 
    ${icons_HEADERS_MOC} 
    ${icons_FORMS_HEADERS} 
    ${icons_RESOURCES_RCC})


TARGET_LINK_LIBRARIES(icons_gui ${QT_LIBRARIES})

