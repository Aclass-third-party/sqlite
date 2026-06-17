add_library(sqlite3 STATIC
    sqlite3.c
)

target_include_directories(sqlite3 PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
)

target_compile_definitions(sqlite3 PRIVATE
    SQLITE_THREADSAFE=0
    SQLITE_OMIT_LOAD_EXTENSION
    SQLITE_OMIT_DEPRECATED
    SQLITE_DEFAULT_MEMSTATUS=0
)

set_target_properties(sqlite3 PROPERTIES
    C_VISIBILITY_PRESET hidden
)

install(TARGETS sqlite3
    LIBRARY   DESTINATION lib
    ARCHIVE   DESTINATION lib
    FILE_SET HEADERS DESTINATION include
)
