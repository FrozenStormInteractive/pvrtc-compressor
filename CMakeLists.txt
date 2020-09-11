cmake_minimum_required(VERSION 3.4)
project(PvrTcCompressor)

if(WIN32 AND BUILD_SHARED_LIBS)
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
endif()

set(HDRS_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/AlphaBitmap.h
    ${CMAKE_CURRENT_SOURCE_DIR}/BitScale.h
    ${CMAKE_CURRENT_SOURCE_DIR}/BitUtility.h
    ${CMAKE_CURRENT_SOURCE_DIR}/Bitmap.h
    ${CMAKE_CURRENT_SOURCE_DIR}/ColorRgba.h
    ${CMAKE_CURRENT_SOURCE_DIR}/Interval.h
    ${CMAKE_CURRENT_SOURCE_DIR}/MortonTable.h
    ${CMAKE_CURRENT_SOURCE_DIR}/Point2.h
    ${CMAKE_CURRENT_SOURCE_DIR}/PvrTcDecoder.h
    ${CMAKE_CURRENT_SOURCE_DIR}/PvrTcEncoder.h
    ${CMAKE_CURRENT_SOURCE_DIR}/PvrTcPacket.h
    ${CMAKE_CURRENT_SOURCE_DIR}/RgbBitmap.h
    ${CMAKE_CURRENT_SOURCE_DIR}/RgbaBitmap.h
)
set(SRCS_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/BitScale.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/MortonTable.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/PvrTcDecoder.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/PvrTcEncoder.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/PvrTcPacket.cpp
)
add_library(pvrtccompressor ${SRCS_FILES} ${HDRS_FILES})
target_include_directories(pvrtccompressor PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
set_property(TARGET pvrtccompressor PROPERTY CXX_STANDARD 11)

install(TARGETS pvrtccompressor
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)
install(FILES ${HDRS_FILES} DESTINATION include)
