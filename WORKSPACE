workspace(
    name = "com_kindlyops_bazel_cross_docker",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_go",
    urls = ["https://github.com/bazelbuild/rules_go/archive/v0.20.2.tar.gz"],
    strip_prefix = "rules_go-0.20.2",
    sha256 = "c92e9be17b8f5d3a5cd4b0549a92c4835a37388b50f007c9cdec9f4ad7baf1f4",
)

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

go_rules_dependencies()

go_register_toolchains(
    go_version = "1.13.3",
)

http_archive(
    name = "bazel_gazelle",
    urls = ["https://github.com/bazelbuild/bazel-gazelle/archive/v0.19.1.tar.gz"],
    strip_prefix = "bazel-gazelle-0.19.1",
    sha256 = "d987004a72697334a095bbaa18d615804a28280201a50ed6c234c40ccc41e493",
)

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies", "go_repository")

gazelle_dependencies()

http_archive(
    name = "io_bazel_rules_docker",
    urls = ["https://github.com/bazelbuild/rules_docker/archive/v0.12.1.tar.gz"],
    strip_prefix = "rules_docker-0.12.1",
    sha256 = "14ac30773fdb393ddec90e158c9ec7ebb3f8a4fd533ec2abbfd8789ad81a284b",
)

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load(
    "@io_bazel_rules_docker//go:image.bzl",
    go_image_repos = "repositories",
)

go_image_repos()

go_repository(
    name = "com_github_gorilla_websocket",
    importpath = "github.com/gorilla/websocket",
    sum = "h1:q7AeDBpnBk8AogcD4DSag/Ukw/KV+YhzLj2bP5HvKCM=",
    version = "v1.4.1",
)

go_repository(
    name = "com_github_containous_whoami",
    importpath = "github.com/containous/whoami",
    patch_args = ["-p1"],
    patches = ["//:whoami.BUILD.patch"],
    sum = "h1:67C6ZyBsINZJW5OC00Z5aX2caOC1++UuHdoHz4wb9dw=",
    version = "v1.4.0",
)
