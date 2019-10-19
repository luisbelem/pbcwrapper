cmake_minimum_required(VERSION 3.13)
project(pbcpp CXX)


set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "-g -O2 -Wall")
include(GNUInstallDirs)

add_library(pbcpp SHARED
        G.cc
        G1.cc
        G2.cc
        GT.cc
        Pairing.cc
        PPPairing.cc
        Zr.cc)
        

set_target_properties(pbcpp PROPERTIES LINKER_LANGUAGE CXX)
#  PUBLIC_HEADER G.h G1.h G2.h GT.h Pairing.h PBC.h PBCExceptions.h PPPairing.h Zr.h)

target_link_libraries(pbcpp  -lpbc -lgmp)

#configure_file(pbcpp.pc.in pbcpp.pc @ONLY)

install(TARGETS pbcpp DESTINATION lib)

#install(FILES ${CMAKE_BINARY_DIR}/pbcpp.pc DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
install(FILES G.h G1.h G2.h GT.h Pairing.h PBC.h PBCExceptions.h PPPairing.h Zr.h DESTINATION include/pbcpp)
