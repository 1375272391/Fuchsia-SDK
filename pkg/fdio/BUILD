# Copyright 2018 The Fuchsia Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.

# DO NOT MANUALLY EDIT!
# Generated by //scripts/sdk/bazel/generate.py.

licenses(["notice"])


package(default_visibility = ["//visibility:public"])

load("//build_defs:package_files.bzl", "package_files")
load("//build_defs:fuchsia_select.bzl", "fuchsia_select")

# Note: the cc_library / cc_import combo serves two purposes:
#  - it allows the use of a select clause to target the proper architecture;
#  - it works around an issue with cc_import which does not have an "includes"
#    nor a "deps" attribute.
cc_library(
    name = "fdio",
    hdrs = [
        "include/lib/fdio/debug.h",
        "include/lib/fdio/io.h",
        "include/lib/fdio/limits.h",
        "include/lib/fdio/namespace.h",
        "include/lib/fdio/private.h",
        "include/lib/fdio/spawn.h",
        "include/lib/fdio/unsafe.h",
        "include/lib/fdio/util.h",
        "include/lib/fdio/vfs.h",
        "include/lib/fdio/watcher.h",
    ],
    deps = fuchsia_select({
        "//build_defs/target_cpu:x64": [":x64_prebuilts"],
    }) + [
    ],
    strip_include_prefix = "include",
    data = fuchsia_select({
        "//build_defs/target_cpu:x64": [":x64_dist"],
    }),
)

# Architecture-specific targets

cc_import(
    name = "x64_prebuilts",
    shared_library = "arch/x64/lib/libfdio.so",
)

package_files(
    name = "x64_dist",
    contents = {
        "arch/x64/dist/libfdio.so": "lib/libfdio.so",
    },
)
