cmake_minimum_required(VERSION 2.6.4)
project(CFS_HK C)

include_directories(fsw/mission_inc)
include_directories(fsw/platform_inc)
include_directories(fsw/tables)
include_directories(fsw/src)

#required for table msg ids
include_directories(${MISSION_SOURCE_DIR}/sample_defs)


aux_source_directory(fsw/src APP_SRC_FILES)

# Create the app module
add_cfe_app(hk ${APP_SRC_FILES})

if (COMMAND add_cfe_tables)
    include_directories(fsw/tables)
    aux_source_directory(fsw/tables APP_TBL_FILES)
    add_cfe_tables(hk fsw/tables/hk_cpy_tbl.c)
endif(COMMAND add_cfe_tables)
