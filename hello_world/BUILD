load(
    "@rules_rust//rust:defs.bzl",
    "rust_binary",
)
load("@crate_index//:defs.bzl", "aliases", "all_crate_deps")

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
    )
)
