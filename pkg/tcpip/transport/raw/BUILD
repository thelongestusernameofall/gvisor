package(
    licenses = ["notice"],  # Apache 2.0
)

load("//tools/go_generics:defs.bzl", "go_template_instance")
load("//tools/go_stateify:defs.bzl", "go_library")

go_template_instance(
    name = "packet_list",
    out = "packet_list.go",
    package = "raw",
    prefix = "packet",
    template = "//pkg/ilist:generic_list",
    types = {
        "Element": "*packet",
        "Linker": "*packet",
    },
)

go_library(
    name = "raw",
    srcs = [
        "endpoint.go",
        "endpoint_state.go",
        "packet_list.go",
    ],
    importpath = "gvisor.googlesource.com/gvisor/pkg/tcpip/transport/raw",
    imports = ["gvisor.googlesource.com/gvisor/pkg/tcpip/buffer"],
    visibility = ["//visibility:public"],
    deps = [
        "//pkg/log",
        "//pkg/sleep",
        "//pkg/tcpip",
        "//pkg/tcpip/buffer",
        "//pkg/tcpip/header",
        "//pkg/tcpip/stack",
        "//pkg/waiter",
    ],
)

filegroup(
    name = "autogen",
    srcs = [
        "packet_list.go",
    ],
    visibility = ["//:sandbox"],
)
