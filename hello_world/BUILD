load(
    "@rules_rust//rust:defs.bzl",
    "rust_binary",
    "rust_test",
)
load("@crate_index//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//cargo:cargo_build_script.bzl", "cargo_build_script")

rust_binary(
    name = "hello_world",
    srcs = glob(["src/**/*.rs"]),
    aliases = aliases(),
    edition = "2021",
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    deps = all_crate_deps(
        normal = True,
    ) + [
        ":proto_gen"
    ]
)

rust_test(
    name = "hello_world_test",
    aliases = aliases(
        normal_dev = True,
        proc_macro_dev = True,
    ),
    crate = ":hello_world",
    proc_macro_deps = all_crate_deps(
        proc_macro_dev = True,
    ),
    deps = all_crate_deps(
        normal_dev = True,
    ),
)

cargo_build_script(
    name = "proto_gen",
    srcs = [
        "build.rs",
    ],
    aliases = aliases(build = True),
    data = [
    ],
    proc_macro_deps = all_crate_deps(
        build_proc_macro = True,
    ),
    deps = all_crate_deps(
        build = True,
    ),
)
