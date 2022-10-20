#-------USER STUFF-------#
#Set the name of the lab as the lab exercice
#example: for Exercise 1:  project(E01)
project(EZZ)

add_executable(${PROJECT_NAME} main.c)
set(FILES)

#-------NON-USER STUFF-------#
#copies the file inside export folder
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../${GLOBAL_PROJECT_NAME}_export/${PROJECT_NAME}/)

#Removes from exported the CMakeLists.txt
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E remove
        ${CMAKE_CURRENT_SOURCE_DIR}/../${GLOBAL_PROJECT_NAME}_export/${PROJECT_NAME}/CMakeLists.txt)

foreach(file ${FILES})
    add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
            COMMAND ${CMAKE_COMMAND} -E copy_if_different
            ${CMAKE_CURRENT_SOURCE_DIR}/${file} $<TARGET_FILE_DIR:${PROJECT_NAME}>/${file}
            )
endforeach()
