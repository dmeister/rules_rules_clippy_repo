load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive", "http_file", "http_jar")


http_archive(
    name = "rules_rust",
    sha256 = "049fe1866e36f7c46cd266b66bad160a9a792e90e5ddd2baeae48fadeea94832",  # pragma: allowlist secret
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/0.34.0/rules_rust-v0.34.0.tar.gz"],
)


BAZEL_TOOLCHAIN_TAG = "0.8.2"
BAZEL_TOOLCHAIN_SHA = "0fc3a2b0c9c929920f4bed8f2b446a8274cad41f5ee823fd3faa0d7641f20db0"  # pragma: allowlist secret

http_archive(
    name = "com_grail_bazel_toolchain",
    sha256 = BAZEL_TOOLCHAIN_SHA,
    strip_prefix = "bazel-toolchain-{tag}".format(tag = BAZEL_TOOLCHAIN_TAG),
    canonical_id = BAZEL_TOOLCHAIN_TAG,
    url = "https://github.com/grailbio/bazel-toolchain/archive/{tag}.tar.gz".format(tag = BAZEL_TOOLCHAIN_TAG),
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")
rules_rust_dependencies()

rust_register_toolchains(
    edition = "2021",
    versions = ["1.74.1"],
)

load("@com_grail_bazel_toolchain//toolchain:deps.bzl", "bazel_toolchain_dependencies")

bazel_toolchain_dependencies()

load("@com_grail_bazel_toolchain//toolchain:rules.bzl", "llvm_toolchain")

llvm_toolchain(
    name = "llvm_toolchain",
    llvm_version = "13.0.1",
    opt_compile_flags = {
        "linux-x86_64": [
            "-DNDEBUG",
            "-O3",
        ],
    },
    stdlib = {
        "linux-x86_64": "stdc++",
    },
)

load("@llvm_toolchain//:toolchains.bzl", "llvm_register_toolchains")

llvm_register_toolchains()


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