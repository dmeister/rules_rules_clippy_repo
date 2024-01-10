load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_rust",
    sha256 = "049fe1866e36f7c46cd266b66bad160a9a792e90e5ddd2baeae48fadeea94832",  # pragma: allowlist secret
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/0.34.0/rules_rust-v0.34.0.tar.gz"],
)


load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")
rules_rust_dependencies()

rust_register_toolchains(
    edition = "2021",
    versions = ["1.74.1"],
)

load("@rules_rust//crate_universe:defs.bzl", "crates_repository")
crates_repository(
        name = "crate_index",
        cargo_lockfile = "//:Cargo.lock",
        lockfile = "//:Cargo.Bazel.lock",
        manifests = [
            "//:Cargo.toml",
            "//hello_world:Cargo.toml",
        ],
    )

load("@crate_index//:defs.bzl", "crate_repositories")

crate_repositories()