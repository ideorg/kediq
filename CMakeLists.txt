cmake_minimum_required(VERSION 3.22)

project(kediq)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_AUTOMOC ON)
#set(CMAKE_AUTORCC ON)
#set(CMAKE_AUTOUIC ON)

set (my_list TextEditor;Parts;XmlGui;SyntaxHighlighting)

foreach (my_entry IN LISTS my_list)
    list(APPEND kfincludes "/usr/include/KF5/K${my_entry}")
    list(APPEND kflibs "KF5${my_entry}")
endforeach()

find_package(Qt5 COMPONENTS
        Widgets
        REQUIRED)

add_executable(${PROJECT_NAME} main.cpp MainWindow.cpp)

target_include_directories(${PROJECT_NAME} PRIVATE
        ${kfincludes}
)

target_link_libraries(${PROJECT_NAME} PRIVATE
        Qt5::Widgets
        ${kflibs}
)
