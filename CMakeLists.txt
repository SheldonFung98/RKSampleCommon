cmake_minimum_required(VERSION 3.16)
project(sample_comm)

option(BUILD_ISP_2 "Build ISP 2.0" OFF)
option(BUILD_ISP_3 "Build ISP 3.0" OFF)
add_definitions(-DRKAIQ)

set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR})
include_directories(
    ${RKMEDIA_INCLUDE_DIR}
    ${RKMEDIA_INCLUDE_DIR}/rockchip
    ${RKMEDIA_INCLUDE_DIR}/rkaiq
    ${RKMEDIA_INCLUDE_DIR}/rkaiq/xcore
    ${RKMEDIA_INCLUDE_DIR}/rkaiq/smartlr
    ${RKMEDIA_INCLUDE_DIR}/rkaiq/algos
    ${RKMEDIA_INCLUDE_DIR}/rkaiq/ipc_server
    ${RKMEDIA_INCLUDE_DIR}/rkaiq/common
)

if(BUILD_ISP_2)
    add_library(${PROJECT_NAME} STATIC
        src/isp2.x/sample_common_isp.c
    )
    target_include_directories(${PROJECT_NAME} PUBLIC
        include/isp2.x
        ${RKMEDIA_INCLUDE_DIR}/easymedia
        ${RKMEDIA_INCLUDE_DIR}/rkaiq/uAPI
        ${RKMEDIA_INCLUDE_DIR}/rkaiq/iq_parser
    )
    install(TARGETS ${PROJECT_NAME} DESTINATION lib/isp2.x)
endif()

if(BUILD_ISP_3)
    file(GLOB SOURCES "src/*.c")
    add_library(${PROJECT_NAME} STATIC
        ${SOURCES}
        src/isp3.x/sample_comm_isp.c
    )
    target_include_directories(${PROJECT_NAME} PUBLIC
        include/isp3.x
        ${RKMEDIA_INCLUDE_DIR}/rkaiq/uAPI2
        ${RKMEDIA_INCLUDE_DIR}/rkaiq/iq_parser_v2
    )
    install(TARGETS ${PROJECT_NAME} DESTINATION lib/isp3.x)
endif()