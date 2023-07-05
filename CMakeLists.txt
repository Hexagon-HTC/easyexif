project(easyexif)
cmake_minimum_required(VERSION 3.0)

add_library(easyexif exif.cpp exif.h)

target_include_directories(easyexif PUBLIC
			$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>
            $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)

set_target_properties(easyexif PROPERTIES PUBLIC_HEADER exif.h)
set_target_properties(easyexif PROPERTIES LIBRARY_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin/Release)
set_target_properties(easyexif PROPERTIES LIBRARY_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin/Debug)
set_target_properties(easyexif PROPERTIES RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin/Release)
set_target_properties(easyexif PROPERTIES RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin/Debug)
set_target_properties(easyexif PROPERTIES ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin/Release)
set_target_properties(easyexif PROPERTIES ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin/Debug)
set_target_properties(easyexif PROPERTIES PDB_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin/Release)
set_target_properties(easyexif PROPERTIES PDB_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin/Debug)
set_target_properties(easyexif PROPERTIES COMPILE_PDB_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin/Release)
set_target_properties(easyexif PROPERTIES COMPILE_PDB_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin/Debug)
set_target_properties(easyexif PROPERTIES OUTPUT_NAME easyexif)
set_target_properties(easyexif PROPERTIES ARCHIVE_OUTPUT_NAME easyexif)
set_target_properties(easyexif PROPERTIES RUNTIME_OUTPUT_NAME easyexif)
set_target_properties(easyexif PROPERTIES LIBRARY_OUTPUT_NAME easyexif)
set_target_properties(easyexif PROPERTIES PDB_NAME easyexif)
set_target_properties(easyexif PROPERTIES COMPILE_PDB_NAME easyexif)

install(TARGETS easyexif EXPORT easyexif
			ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
			RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
			LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
			PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/easyexif)

install(EXPORT easyexif NAMESPACE easyexif:: DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/${CMAKE_PROJECT_NAME} FILE easyexifConfig.cmake)

if(MSVC)
	install(FILES ${CMAKE_BINARY_DIR}/bin/Debug/easyexif.pdb DESTINATION ${CMAKE_INSTALL_LIBDIR}/Debug CONFIGURATIONS Debug)
endif(MSVC)

target_include_directories(easyexif PRIVATE ${CMAKE_SOURCE_DIR})
