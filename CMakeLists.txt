cmake_minimum_required(VERSION 3.0)

#-------USER VARIABLES-------#
#Set ZZ as 01, 02, 03...
set(GLOBAL_PROJECT_NAME LZZ)
project(${GLOBAL_PROJECT_NAME})
#If needed, set another C standard
set(CMAKE_C_STANDARD 99)
#Add or remove your subdirectories (exercises)!
set(DIRECTORIES E01 E02 E03 E04)
#----------------------------#

#-------NON USER SPACE-------#
#Do not touch these unless you are sure about what you are doing!
foreach(DIR ${DIRECTORIES})
    add_subdirectory(${DIR})
    message(${DIR} " will be built in the project")
endforeach()



