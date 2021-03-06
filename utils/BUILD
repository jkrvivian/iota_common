package(default_visibility = ["//visibility:public"])

config_setting(
    name = "windows_platform",
    constraint_values = [
        "@bazel_tools//platforms:windows",
    ],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "bundle_miner",
    srcs = ["bundle_miner.c"],
    hdrs = ["bundle_miner.h"],
    deps = [
        "//common:defs",
        "//common:errors",
        "//common/crypto/iss:normalize",
        "//common/crypto/kerl",
        "//common/model:transaction",
        "//common/trinary:bytes",
        "//common/trinary:trit_long",
        "//common/trinary:trits",
        "//utils:macros",
        "//utils:system",
        "//utils/handles:thread",
    ],
)

cc_library(
    name = "export",
    hdrs = ["export.h"],
)

cc_library(
    name = "windows",
    hdrs = ["windows.h"],
)

cc_library(
    name = "forced_inline",
    hdrs = ["forced_inline.h"],
)

cc_library(
    name = "logger_helper",
    srcs = ["logger_helper.c"],
    hdrs = ["logger_helper.h"],
    copts = ["-DLOGGER_ENABLE"],
    deps = [
        "//common:errors",
        "//utils/handles:lock",
        "@com_github_embear_logger//:logger",
    ],
)

cc_library(
    name = "macros",
    hdrs = ["macros.h"],
    deps = select({
        ":windows_platform": ["//utils:windows"],
        "//conditions:default": [],
    }),
)

cc_library(
    name = "merkle",
    srcs = ["merkle.c"],
    hdrs = ["merkle.h"],
    deps = ["//common/crypto/iss/v2:iss_curl"],
)

cc_library(
    name = "system",
    srcs = ["system.c"],
    hdrs = ["system.h"],
    deps = select({
        ":windows_platform": ["//utils:windows"],
        "//conditions:default": [],
    }),
)

cc_library(
    name = "time",
    srcs = ["time.c"],
    hdrs = ["time.h"],
    deps = select({
        ":windows_platform": ["//utils:windows"],
        "//conditions:default": [],
    }),
)

cc_library(
    name = "hash_maps",
    srcs = ["hash_indexed_map.c"],
    hdrs = ["hash_indexed_map.h"],
    deps = [
        "//common:errors",
        "//common/trinary:flex_trit",
        "//utils/containers/hash:hash243_set",
        "@com_github_uthash//:uthash",
    ],
)

cc_library(
    name = "memset_safe",
    srcs = ["memset_safe.c"],
    hdrs = ["memset_safe.h"],
    deps = ["//common:errors"],
)

cc_library(
    name = "char_buffer",
    srcs = ["char_buffer.c"],
    hdrs = ["char_buffer.h"],
    deps = ["//common:errors"],
)

cc_library(
    name = "input_validators",
    srcs = ["input_validators.c"],
    hdrs = ["input_validators.h"],
    deps = [
        "//common/model:transaction",
        "//common/trinary:trits",
        "//common/trinary:tryte",
    ],
)
