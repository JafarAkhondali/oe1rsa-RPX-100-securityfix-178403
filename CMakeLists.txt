# SPDX-FileCopyrightText: 2022 Roland Schwarz <oe1rsa@blackspace.at>
#
# SPDX-License-Identifier: GPL-3.0-or-later

cmake_minimum_required(VERSION 3.18.4)

project(rpx-100 VERSION 0.0.0)

# Make sure our local CMake Modules path comes first.
list(INSERT CMAKE_MODULE_PATH 0 ${PROJECT_SOURCE_DIR}/cmake/Modules)

find_package(Threads               REQUIRED)
find_package(Libwebsockets 4.0.20  REQUIRED)
find_package(LimeSuite     20.10.0 REQUIRED)
find_package(LiquidDSP     1.3.2   REQUIRED)

add_executable(RPX-100
  RPX-100.cpp
  SDRsamples.cpp
  WebSocketServer.cpp
  Util.cpp
  sockets/ClientSocket.cpp
  sockets/ServerSocket.cpp
  sockets/Socket.cpp
)

target_link_libraries(RPX-100
  LimeSuite
  Threads::Threads
  LiquidDSP::LiquidDSP
  ${LIBWEBSOCKETS_LIBRARIES}
)

install(TARGETS RPX-100)

add_executable(RPX-100-Test
  RPX-100-Test.cpp
  SDR-Test.cpp
  WebSocketServer.cpp
  Util.cpp
  sockets/ClientSocket.cpp
  sockets/ServerSocket.cpp
  sockets/Socket.cpp
  )

target_link_libraries(RPX-100-Test
  LimeSuite
  Threads::Threads
  LiquidDSP::LiquidDSP
  ${LIBWEBSOCKETS_LIBRARIES}
)

install(TARGETS RPX-100-Test)

add_executable(RPX-100-Beacon
  RPX-100-Beacon.cpp
  SDRsamples-Beacon.cpp
  WebSocketServer.cpp
  Util.cpp
  sockets/ClientSocket.cpp
  sockets/ServerSocket.cpp
  sockets/Socket.cpp
  )

target_link_libraries(RPX-100-Beacon
  LimeSuite
  Threads::Threads
  LiquidDSP::LiquidDSP
  ${LIBWEBSOCKETS_LIBRARIES}
)

install(TARGETS RPX-100-Beacon)

add_executable(RPX-100-Beacon-reorganized
  RPX-100-Beacon-reorganized.cpp
  WebSocketServer.cpp
  Util.cpp
  sockets/ClientSocket.cpp
  sockets/ServerSocket.cpp
  sockets/Socket.cpp
  )

target_link_libraries(RPX-100-Beacon-reorganized
  LimeSuite
  Threads::Threads
  LiquidDSP::LiquidDSP
  ${LIBWEBSOCKETS_LIBRARIES}
)

install(TARGETS RPX-100-Beacon-reorganized)

add_executable(RPX-100-FSK
  RPX-100-FSK.cpp
  SDRsamples-FSK.cpp
)

target_link_libraries(RPX-100-FSK
  LimeSuite
  Threads::Threads
  LiquidDSP::LiquidDSP
)

install(TARGETS RPX-100-FSK)
