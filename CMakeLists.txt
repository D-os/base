add_library(base SHARED
  "chrono_utils.cpp"
  "cmsg.cpp"
  "file.cpp"
  "logging.cpp"
  "mapped_file.cpp"
  "parsenetaddress.cpp"
  "properties.cpp"
  "quick_exit.cpp"
  "stringprintf.cpp"
  "strings.cpp"
  "threads.cpp"
  "test_utils.cpp"

  "errors_unix.cpp"
)
target_compile_options(base PRIVATE -Wexit-time-destructors -D_FILE_OFFSET_BITS=64)
#target_link_libraries(base log)

add_executable(libbase_tests
  "cmsg_test.cpp"
  "endian_test.cpp"
  "errors_test.cpp"
  "file_test.cpp"
  "logging_test.cpp"
  "macros_test.cpp"
  "mapped_file_test.cpp"
  "parsedouble_test.cpp"
  "parseint_test.cpp"
  "parsenetaddress_test.cpp"
  "properties_test.cpp"
  "quick_exit_test.cpp"
  "scopeguard_test.cpp"
  "stringprintf_test.cpp"
  "strings_test.cpp"
  "test_main.cpp"
  "test_utils_test.cpp"

  "chrono_utils_test.cpp"
)
target_include_directories(libbase_tests PUBLIC
  "${EXTERNAL_GOOGLETEST_DIR}/googletest/include"
  "${EXTERNAL_GOOGLETEST_DIR}/googlemock/include"
)
target_link_libraries(libbase_tests gtest_main gtest base)
