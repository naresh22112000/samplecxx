load(
    "//:build/rust.bzl",
    rust_binary = "third_party_rust_binary",
    rust_library = "third_party_rust_library",
)
load("@bazel_tools//tools/build_defs/pkg:pkg.bzl", "pkg_tar")

rust_library(
    name = "anyhow",
    srcs = glob(["vendor/anyhow-1.0.26/src/**"]),
    crate_features = ["std"],
    visibility = ["//visibility:public"],
)

rust_library(
    name = "bitflags",
    srcs = glob(["vendor/bitflags-1.2.1/src/**"]),
)

rust_library(
    name = "cc",
    srcs = glob(["vendor/cc-1.0.50/src/**"]),
    visibility = ["//visibility:public"],
)

rust_library(
    name = "clap",
    srcs = glob(["vendor/clap-2.33.0/src/**"]),
    edition = "2015",
    deps = [
        ":bitflags",
        ":textwrap",
        ":unicode_width",
    ],
)

rust_library(
    name = "codespan",
    srcs = glob(["vendor/codespan-0.7.0/src/**"]),
    visibility = ["//visibility:public"],
    deps = [":unicode_segmentation"],
)

rust_library(
    name = "codespan_reporting",
    srcs = glob(["vendor/codespan-reporting-0.7.0/src/**"]),
    visibility = ["//visibility:public"],
    deps = [
        ":codespan",
        ":termcolor",
        ":unicode_width",
    ],
)

rust_library(
    name = "heck",
    srcs = glob(["vendor/heck-0.3.1/src/**"]),
    edition = "2015",
    deps = [":unicode_segmentation"],
)

rust_library(
    name = "lazy_static",
    srcs = glob(["vendor/lazy_static-1.4.0/src/**"]),
)

rust_library(
    name = "link_cplusplus",
    srcs = glob(["vendor/link-cplusplus-1.0.1/src/**"]),
    visibility = ["//visibility:public"],
)

rust_library(
    name = "proc_macro_error",
    srcs = glob(["vendor/proc-macro-error-0.4.9/src/**"]),
    rustc_flags = ["--cfg=use_fallback"],
    deps = [
        ":proc_macro2",
        ":proc_macro_error_attr",
        ":quote",
        ":syn",
    ],
)

rust_library(
    name = "proc_macro_error_attr",
    srcs = glob(["vendor/proc-macro-error-attr-0.4.9/src/**"]),
    crate_type = "proc-macro",
    deps = [
        ":proc_macro2",
        ":quote",
        ":rustversion",
        ":syn",
        ":syn_mid",
    ],
)

rust_library(
    name = "proc_macro2",
    srcs = glob(["vendor/proc-macro2-1.0.8/src/**"]),
    crate_features = [
        "proc-macro",
        "span-locations",
    ],
    rustc_flags = [
        "--cfg=span_locations",
        "--cfg=use_proc_macro",
        "--cfg=wrap_proc_macro",
    ],
    visibility = ["//visibility:public"],
    deps = [":unicode_xid"],
)

rust_library(
    name = "quote",
    srcs = glob(["vendor/quote-1.0.2/src/**"]),
    crate_features = ["proc-macro"],
    visibility = ["//visibility:public"],
    deps = [":proc_macro2"],
)

rust_library(
    name = "rustversion",
    srcs = glob(["vendor/rustversion-1.0.2/src/**"]),
    crate_type = "proc-macro",
    out_dir_tar = ":rustversion_buildscript_outdir",
    deps = [
        ":proc_macro2",
        ":quote",
        ":syn",
    ],
)

rust_binary(
    name = "rustversion_buildscript",
    srcs = glob(["vendor/rustversion-1.0.2/build/**"]),
    crate_root = "vendor/rustversion-1.0.2/build/build.rs",
)

pkg_tar(
    name = "rustversion_buildscript_outdir",
    srcs = [":rustversion_buildscript_run"],
    extension = "tar.gz",
)

genrule(
    name = "rustversion_buildscript_run",
    outs = ["version.rs"],
    cmd = "OUT_DIR=$(@D) $(location :rustversion_buildscript)",
    tools = [":rustversion_buildscript"],
)

rust_library(
    name = "structopt",
    srcs = glob(["vendor/structopt-0.3.9/src/**"]),
    visibility = ["//visibility:public"],
    deps = [
        ":clap",
        ":lazy_static",
        ":structopt_derive",
    ],
)

rust_library(
    name = "structopt_derive",
    srcs = glob(["vendor/structopt-derive-0.4.2/src/**"]),
    crate_type = "proc-macro",
    deps = [
        ":heck",
        ":proc_macro2",
        ":proc_macro_error",
        ":quote",
        ":syn",
    ],
)

rust_library(
    name = "syn",
    srcs = glob(["vendor/syn-1.0.15/src/**"]),
    crate_features = [
        "clone-impls",
        "derive",
        "full",
        "parsing",
        "printing",
        "proc-macro",
    ],
    visibility = ["//visibility:public"],
    deps = [
        ":proc_macro2",
        ":quote",
        ":unicode_xid",
    ],
)

rust_library(
    name = "syn_mid",
    srcs = glob(["vendor/syn-mid-0.5.0/src/**"]),
    deps = [
        ":proc_macro2",
        ":quote",
        ":syn",
    ],
)

rust_library(
    name = "termcolor",
    srcs = glob(["vendor/termcolor-1.1.0/src/**"]),
)

rust_library(
    name = "textwrap",
    srcs = glob(["vendor/textwrap-0.11.0/src/**"]),
    deps = [":unicode_width"],
)

rust_library(
    name = "thiserror",
    srcs = glob(["vendor/thiserror-1.0.11/src/**"]),
    visibility = ["//visibility:public"],
    deps = [":thiserror_impl"],
)

rust_library(
    name = "thiserror_impl",
    srcs = glob(["vendor/thiserror-impl-1.0.11/src/**"]),
    crate_type = "proc-macro",
    deps = [
        ":proc_macro2",
        ":quote",
        ":syn",
    ],
)

rust_library(
    name = "unicode_segmentation",
    srcs = glob(["vendor/unicode-segmentation-1.6.0/src/**"]),
    edition = "2015",
)

rust_library(
    name = "unicode_width",
    srcs = glob(["vendor/unicode-width-0.1.7/src/**"]),
)

rust_library(
    name = "unicode_xid",
    srcs = glob(["vendor/unicode-xid-0.2.0/src/**"]),
)