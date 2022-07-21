# Toolkit for working with NK parser.
include (platform/nk)
set (HAVE_READDIR YES)

# Project header.
project_header_default ("STANDARD_GNU_11:YES" "STRICT_WARNINGS:NO")

nk_build_edl_files (vfs_user_edl_files  NK_MODULE "vfs_user" EDL "${CMAKE_SOURCE_DIR}/resources/edl/VfsUser.edl")

if (CMAKE_SYSTEM_PROCESSOR STREQUAL "arm")
    set (BLKDEV "mmc")
else ()
    set (BLKDEV "Ahci0Port")
endif ()

add_executable (VfsUser "src/vfs_user.c" ${CMAKE_SOURCE_DIR}/common/common.c)
add_dependencies (VfsUser vfs_user_edl_files)
target_link_libraries (VfsUser ${vfs_SERVER_LIB} ${vfs_FS_LIB} ${LWEXT4_LIB})
set_target_properties (VfsUser PROPERTIES COMPILE_DEFINITIONS BLKDEV="${BLKDEV}")
