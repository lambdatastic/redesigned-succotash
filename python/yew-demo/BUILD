package(default_visibility = ["//visibility:public"])

py_binary(
    name = "server",
    srcs = ["server.py"],
    data = [
        "//rust/yew-demo:main_wasm",
        "//static/yew-demo:static_bundle",
    ]
)