cmake_minimum_required(VERSION 3.5)
project(ubms_coin VERSION 0.1 LANGUAGES CXX)

###==========================================================
###    ubuntu 22.04 build
###==========================================================




add_subdirectory(src/ubmscoin)
add_subdirectory(src/ubmsdaemon)
add_subdirectory(src/ubmscli)
add_subdirectory(src/ubmsopcode8)
add_subdirectory(src/ubmsopcode32)

