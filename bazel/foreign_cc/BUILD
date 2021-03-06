licenses(["notice"])  # Apache 2

load("//bazel:envoy_build_system.bzl", "envoy_cmake_external", "envoy_package")

envoy_package()

envoy_cmake_external(
    name = "ares",
    cache_entries = {
        "CARES_SHARED": "no",
        "CARES_STATIC": "on",
        "CMAKE_BUILD_TYPE": "RelWithDebInfo",
    },
    copy_pdb = True,
    lib_source = "@com_github_c_ares_c_ares//:all",
    pdb_name = "c-ares",
    static_libraries = select({
        "//bazel:windows_x86_64": ["cares.lib"],
        "//conditions:default": ["libcares.a"],
    }),
)

envoy_cmake_external(
    name = "event",
    cache_entries = {
        "EVENT__DISABLE_OPENSSL": "on",
        "EVENT__DISABLE_REGRESS": "on",
        "EVENT__LIBRARY_TYPE": "STATIC",
        "CMAKE_BUILD_TYPE": "Release",
    },
    copy_pdb = True,
    lib_source = "@com_github_libevent_libevent//:all",
    static_libraries = select({
        "//bazel:windows_x86_64": ["event.lib"],
        "//conditions:default": [
            "libevent.a",
            "libevent_pthreads.a",
        ],
    }),
)

envoy_cmake_external(
    name = "nghttp2",
    cache_entries = {
        "ENABLE_STATIC_LIB": "on",
        "ENABLE_LIB_ONLY": "on",
        "CMAKE_BUILD_TYPE": "RelWithDebInfo",
        "CMAKE_INSTALL_LIBDIR": "lib",
    },
    cmake_files_dir = "$BUILD_TMPDIR/lib/CMakeFiles",
    copy_pdb = True,
    debug_cache_entries = {"ENABLE_DEBUG": "on"},
    lib_source = "@com_github_nghttp2_nghttp2//:all",
    pdb_name = "nghttp2_static",
    static_libraries = select({
        "//bazel:windows_x86_64": ["nghttp2_static.lib"],
        "//conditions:default": ["libnghttp2_static.a"],
    }),
)

envoy_cmake_external(
    name = "yaml",
    cache_entries = {
        "YAML_CPP_BUILD_TESTS": "off",
        "YAML_CPP_BUILD_TOOLS": "off",
        "CMAKE_BUILD_TYPE": "RelWithDebInfo",
    },
    lib_source = "@com_github_jbeder_yaml_cpp//:all",
    static_libraries = select({
        "//bazel:windows_dbg_build": ["libyaml-cppmdd.lib"],
        "//bazel:windows_fastbuild_build": ["libyaml-cppmd.lib"],
        "//bazel:windows_opt_build": ["libyaml-cppmd.lib"],
        "//conditions:default": ["libyaml-cpp.a"],
    }),
)

envoy_cmake_external(
    name = "zlib",
    cache_entries = {
        "CMAKE_BUILD_TYPE": "RelWithDebInfo",
    },
    copy_pdb = True,
    lib_source = "@com_github_madler_zlib//:all",
    pdb_name = "zlibstatic",
    static_libraries = select({
        "//bazel:windows_dbg_build": ["zlibstaticd.lib"],
        "//bazel:windows_fastbuild_build": ["zlibstatic.lib"],
        "//bazel:windows_opt_build": ["zlibstatic.lib"],
        "//conditions:default": ["libz.a"],
    }),
)
