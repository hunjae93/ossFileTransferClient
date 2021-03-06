cmake_minimum_required (VERSION 3.8)

project ("FTC")



list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/GCR_CMake/macros)
include (GlibCompileResourcesSupport)

FIND_PACKAGE(PkgConfig REQUIRED)
PKG_CHECK_MODULES(GTK3 REQUIRED gtk+-3.0)
PKG_CHECK_MODULES(WEBKIT REQUIRED webkit2gtk-4.0)
PKG_CHECK_MODULES(WEBKIT_EXT REQUIRED webkit2gtk-web-extension-4.0)
PKG_CHECK_MODULES(UUID REQUIRED uuid)
FIND_PACKAGE(OpenSSL REQUIRED)
FIND_PACKAGE(X11 REQUIRED)

INCLUDE_DIRECTORIES(${GTK3_INCLUDE_DIRS} ${WEBKIT_INCLUDE_DIRS} ${WEBKIT_EXT_INCLUDE_DIRS} ${OPENSSL_INCLUDE_DIRS} ${X11_INCLUDE_DIRS} /usr/include/libsoup-2.4 /usr/include/json-glib-1.0)
LINK_DIRECTORIES(${GTK3_LIBRARY_DIRS} ${WEBKIT_LIBRARY_DIRS} ${WEBKIT_EXT_LIBRARY_DIRS} ${OPENSSL_LIBRARY_DIRS} ${X11_LIBRARY_DIRS} ${CMAKE_SOURCE_DIR}/build/lib)
ADD_DEFINITIONS(${GTK3_CFLAGS_OTHER} ${WEBKIT_CFLAGS_OTHER} ${WEBKIT_EXT_CFLAGS_OTHER} ${OPENSSL_CFLAGS_OTHER} ${X11_CFLAGS_OTHER})

set(EXECUTABLE_OUTPUT_PATH "${CMAKE_SOURCE_DIR}/build/bin")
set(LIBRARY_OUTPUT_PATH "${CMAKE_SOURCE_DIR}/build/lib/ftc/")

add_subdirectory ("src")