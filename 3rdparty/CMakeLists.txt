include(FetchContent)

function(download_requirement require_name repository_url tag)
  message(STATUS "Downloading ${require_name}")
  include(FetchContent)
  FetchContent_Declare(
    ${require_name}
    GIT_REPOSITORY ${repository_url}
    GIT_TAG        ${tag}
  )
  FetchContent_MakeAvailable(${require_name})
endfunction()

download_requirement(
  "googletest"
  "https://github.com/google/googletest.git"
  "v1.12.x"
)
download_requirement(
  "yaml-cpp"
  "https://github.com/jbeder/yaml-cpp.git"
  "yaml-cpp-0.7.0"
)
download_requirement(
  "tomlplusplus"
  "https://github.com/marzer/tomlplusplus.git"
  "v3.4.0"
)
download_requirement(
  "jsoncpp"
  "https://github.com/open-source-parsers/jsoncpp.git"
  "1.9.5"
)
download_requirement(
  "fmtlib"
  "https://github.com/fmtlib/fmt.git"
  "10.1.1"
)
download_requirement(
  "expected"
  "https://github.com/TartanLlama/expected.git"
  "v1.1.0"
)
download_requirement(
  "range-v3"
  "https://github.com/ericniebler/range-v3.git"
  "0.12.0"
)
