# Copyright (c) the JPEG XL Project Authors. All rights reserved.
#
# Use of this source code is governed by a BSD-style
# license that can be found in the LICENSE file.

# Example project using libjxl.

cmake_minimum_required(VERSION 3.10)

project(SAMPLE_LIBJXL LANGUAGES C CXX)

# Use pkg-config to find libjxl.
find_package(PkgConfig)
pkg_check_modules(Jxl REQUIRED IMPORTED_TARGET libjxl libjxl_cms libjxl_threads)

# Build the example encoder/decoder binaries using the default shared libraries
# installed.
add_executable(decode_exif_metadata decode_exif_metadata.cc)
target_link_libraries(decode_exif_metadata PkgConfig::Jxl)

add_executable(decode_oneshot decode_oneshot.cc)
target_link_libraries(decode_oneshot PkgConfig::Jxl)

add_executable(decode_progressive decode_progressive.cc)
target_link_libraries(decode_progressive PkgConfig::Jxl)

add_executable(encode_oneshot encode_oneshot.cc)
target_link_libraries(encode_oneshot PkgConfig::Jxl)
