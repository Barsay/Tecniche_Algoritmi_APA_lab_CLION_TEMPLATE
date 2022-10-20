project(E01 ) #Set ZZ as 01, 02, 103...

add_executable(${PROJECT_NAME} main.c)


#-------NON-USER STUFF-------#

#This script copies the files inside the export folder
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../${GLOBAL_PROJECT_NAME}_export/${PROJECT_NAME}/)

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E remove
        ${CMAKE_CURRENT_SOURCE_DIR}/../${GLOBAL_PROJECT_NAME}_export/${PROJECT_NAME}/CMakeLists.txt)
