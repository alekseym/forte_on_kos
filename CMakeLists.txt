cmake_minimum_required (VERSION 3.12)
project (forte)

# Initialize CMake library for Kaspersky OS SDK.
include (platform)
initialize_platform ()

# Toolchain for work with NK-parser.
include (platform/nk)

# Connect artifact installation functions.
include (platform/install)

include (platform/nk)
#nk_build_edl_files (separate_storage_vfs_user  NK_MODULE "separate_storage" EDL "resources/edl/VfsUser.edl")


if (KOS)
    # Attach a package with the virtual file system implementation.
    find_package (vfs REQUIRED COMPONENTS FS_LIB CLIENT_LIB SERVER_LIB)
    include_directories (${vfs_INCLUDE})

    # Attach a package with the DNET file system implementation.
    find_package (dnet REQUIRED COMPONENTS IMPLEMENTATION_LIB)

# Connect a package that imports components 
# to work with the ext2/ext3/ext4 file systems.
    find_package (LWEXT4 REQUIRED)
    include_directories (${LWEXT4_INCLUDE})

    include_directories (common)


    add_subdirectory (forte)
    add_subdirectory (vfs_user)

endif ()

#add_subdirectory (server)

if (KOS)
    # Binary image of KasperskyOS.
    add_subdirectory (einit)
endif ()
