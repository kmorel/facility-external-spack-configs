cmake_minimum_required(VERSION 3.15)

project(facility-external-spack-configs
        LANGUAGES NONE
        DESCRIPTION "spack configs for DOE Facilities")

set(all_facilities frontier perlmutter)

set(FACILITY "all" CACHE STRING "The facility configs to install")
set_property(CACHE FACILITY PROPERTY STRINGS
        "all" ${all_facilities})

install(DIRECTORY "$<IF:$<STREQUAL:${FACILITY},all>,${all_facilities},${FACILITY}>" 
        DESTINATION spack/configs/facilities)
