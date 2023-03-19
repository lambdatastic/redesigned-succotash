package(default_visibility = ["//visibility:public"])

load("@rules_rust//rust:defs.bzl", "rust_binary")
load("@rules_rust//wasm_bindgen:wasm_bindgen.bzl", "rust_wasm_bindgen")

rust_binary(
    name = "main",
    srcs = [
        "main.rs"
    ],
    edition = "2018",
    deps = [
        "@crate_index//:yew",
    ],
)

rust_wasm_bindgen(
    name = "main_wasm",
    target = "web",
    wasm_file = ":main",
)