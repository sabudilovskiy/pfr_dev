# Copyright 2020 Peter Dimov
# Copyright (c) 2016-2024 Antony Polukhin
#
# Distributed under the Boost Software License, Version 1.0.
# https://www.boost.org/LICENSE_1_0.txt

cmake_minimum_required(VERSION 3.5...3.16)

project(boost_pfr_dev VERSION "${BOOST_SUPERPROJECT_VERSION}" LANGUAGES CXX)

add_library(boost_pfr_dev INTERFACE)
add_library(Boost::pfr_dev ALIAS boost_pfr_dev)

target_include_directories(boost_pfr_dev INTERFACE include)

if (CMAKE_VERSION VERSION_GREATER_EQUAL "3.28.0" AND BUILD_MODULE)
    add_subdirectory(module)
endif()

if (BUILD_TESTING AND EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/test/CMakeLists.txt")
  add_subdirectory(test)
endif()

