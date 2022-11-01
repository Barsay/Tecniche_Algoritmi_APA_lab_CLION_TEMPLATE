#-------USER STUFF-------#
#Set the name of the lab as the lab exercice
#example: for Exercise 1:  project(E01)
project(EZZ)

#Add source files and headers if needed
#example: add_executable(${PROJECT_NAME} main.c some_header.h another_header.h ../some/folder/header.h)
add_executable(${PROJECT_NAME} main.c)

#Add file names if needed. This enables you to include a file with a relative path and being able to open/include it inside your main.c
#Notice: It is better to add your file in the same folder as your main.c !
#Warning: if you want to set files with absolute path, do not add them here!
#
#example: set(FILES ./inputFile.txt ./anotherInputFile.txt) <- notice the relative path!
#example: you will be now able to do something like #define FILE_PATH "./inputfile.txt" and then fopen(FILE_PATH, ...) without errors!
set(FILES in.txt)

#-------NON USER STUFF-------#
#Do not modify this if you are not sure!

#copies the file inside export folder
add_custom_command(TARGET ${PROJECT_NAME} PRE_BUILD
        DEPENDS ${PROJECT_NAME}
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../${LAB_NAME}_export/${PROJECT_NAME}/)

#Removes from exported the CMakeLists.txt
add_custom_command(TARGET ${PROJECT_NAME} PRE_BUILD
        DEPENDS ${PROJECT_NAME}
        COMMAND ${CMAKE_COMMAND} -E remove
        ${CMAKE_CURRENT_SOURCE_DIR}/../${LAB_NAME}_export/${PROJECT_NAME}/CMakeLists.txt)

foreach(file ${FILES})
    #for every file, copy it in target build directory
    add_custom_command(TARGET ${PROJECT_NAME} PRE_BUILD
            DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/${file}
            COMMAND ${CMAKE_COMMAND} -E copy_if_different
            ${CMAKE_CURRENT_SOURCE_DIR}/${file} $<TARGET_FILE_DIR:${PROJECT_NAME}>/${file}
            )
    #add the file as source property: build will be triggered on file upload
    set_property(SOURCE main.c APPEND PROPERTY OBJECT_DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/${file})
endforeach()
