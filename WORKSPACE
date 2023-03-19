load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name = "rules_rust",
    sha256 = "dc8d79fe9a5beb79d93e482eb807266a0e066e97a7b8c48d43ecf91f32a3a8f3",
    urls = ["https://github.com/bazelbuild/rules_rust/releases/download/0.19.0/rules_rust-v0.19.0.tar.gz"],
)

load("@rules_rust//rust:repositories.bzl", "rules_rust_dependencies", "rust_register_toolchains")
rules_rust_dependencies()
rust_register_toolchains()

load("@rules_rust//crate_universe:repositories.bzl", "crate_universe_dependencies")
crate_universe_dependencies()

load("@rules_rust//crate_universe:defs.bzl", "crate", "crates_repository", "render_config")

crates_repository(
    name = "crate_index",
    cargo_lockfile = "//:cargo.lock",
    lockfile = "//:Cargo.Bazel.lock",
    packages = {
        "yew": crate.spec(
            version = "0.20.0",
            features = [
                "csr"
            ]
        ),
        # Pinned to match the version used by @rules_rust
        "wasm-bindgen": crate.spec(
            version = "= 0.2.83",
        ),
    },
    render_config = render_config(
        default_package_name = ""
    ),
    generate_binaries = True
)

load("@crate_index//:defs.bzl", "crate_repositories")
crate_repositories()

load("@rules_rust//wasm_bindgen:repositories.bzl", "rust_wasm_bindgen_repositories")
rust_wasm_bindgen_repositories()