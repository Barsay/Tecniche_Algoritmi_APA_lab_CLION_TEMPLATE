cmake_minimum_required(VERSION 3.0)

#-------USER VARIABLES-------#
#Set those variables according to your needs
#example set(GLOBAL_PROJECT_NAME L01) for lab01
set(LAB_NAME LZZ)
#Add directory names here!
#example set(DIRECTORIES E01 E02 E03)
set(DIRECTORIES EZZ)

#-------NON USER SPACE-------#
#Don't touch here unless you know what you are doing!
project(${LAB_NAME})
set(CMAKE_C_STANDARD 99)
#Do not touch these unless you are sure about what you are doing!
foreach(DIR ${DIRECTORIES})
    add_subdirectory(${DIR})
    message(${DIR} " will be built in the project")
endforeach()



