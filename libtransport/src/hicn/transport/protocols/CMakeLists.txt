# Copyright (c) 2017-2019 Cisco and/or its affiliates.
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at:
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

list(APPEND HEADER_FILES
  ${CMAKE_CURRENT_SOURCE_DIR}/indexing_manager.h
  ${CMAKE_CURRENT_SOURCE_DIR}/reassembly.h
  ${CMAKE_CURRENT_SOURCE_DIR}/congestion_window_protocol.h
  ${CMAKE_CURRENT_SOURCE_DIR}/packet_manager.h
  ${CMAKE_CURRENT_SOURCE_DIR}/statistics.h
  ${CMAKE_CURRENT_SOURCE_DIR}/rate_estimation.h
  ${CMAKE_CURRENT_SOURCE_DIR}/download_observer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/protocol.h
  ${CMAKE_CURRENT_SOURCE_DIR}/raaqm.h
  ${CMAKE_CURRENT_SOURCE_DIR}/raaqm_data_path.h
  ${CMAKE_CURRENT_SOURCE_DIR}/cbr.h
  ${CMAKE_CURRENT_SOURCE_DIR}/rtc.h
  ${CMAKE_CURRENT_SOURCE_DIR}/rtc_data_path.h
  ${CMAKE_CURRENT_SOURCE_DIR}/manifest_indexing_manager.h
)

list(APPEND SOURCE_FILES
  ${CMAKE_CURRENT_SOURCE_DIR}/reassembly.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/protocol.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/raaqm.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/rate_estimation.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/raaqm_data_path.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/cbr.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/rtc.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/rtc_data_path.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/manifest_indexing_manager.cc
)

set(RAAQM_CONFIG_INSTALL_PREFIX
${CMAKE_INSTALL_PREFIX}/etc/hicn
)

set(raaqm_config_path
  ${RAAQM_CONFIG_INSTALL_PREFIX}/consumer.conf
  PARENT_SCOPE
)

set(TRANSPORT_CONFIG
  ${CMAKE_CURRENT_SOURCE_DIR}/consumer.conf
)

install(
  FILES ${TRANSPORT_CONFIG}
  DESTINATION etc/hicn
  COMPONENT lib${LIBTRANSPORT}
)

set(SOURCE_FILES ${SOURCE_FILES} PARENT_SCOPE)
set(HEADER_FILES ${HEADER_FILES} PARENT_SCOPE)