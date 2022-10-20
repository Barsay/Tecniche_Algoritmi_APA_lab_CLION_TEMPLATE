cmake_minimum_required(VERSION 3.0)

#-------USER VARIABLES-------#
#Set those variables according to your needs
#Set ZZ as 01, 02, 03... eg L01, L02....
set(GLOBAL_PROJECT_NAME LZZ)
#Add or remove your subdirectories (exercises)!
set(DIRECTORIES E01 E02 E03 E04)
#----------------------------#

#-------NON USER SPACE-------#
#Don't touch here unless you know what you are doing!
project(${GLOBAL_PROJECT_NAME})
set(CMAKE_C_STANDARD 99)
#Do not touch these unless you are sure about what you are doing!
foreach(DIR ${DIRECTORIES})
    add_subdirectory(${DIR})
    message(${DIR} " will be built in the project")
endforeach()



