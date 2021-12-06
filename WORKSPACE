workspace(name = "gazelle_demo")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# Download the Go rules.
http_archive(
    name = "io_bazel_rules_go",
    sha256 = "2b1641428dff9018f9e85c0384f03ec6c10660d935b750e3fa1492a281a53b0f",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_go/releases/download/v0.29.0/rules_go-v0.29.0.zip",
        "https://github.com/bazelbuild/rules_go/releases/download/v0.29.0/rules_go-v0.29.0.zip",
    ],
)

# Download Gazelle.
http_archive(
    name = "bazel_gazelle",
    sha256 = "de69a09dc70417580aabf20a28619bb3ef60d038470c7cf8442fafcf627c21cb",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-gazelle/releases/download/v0.24.0/bazel-gazelle-v0.24.0.tar.gz",
        "https://github.com/bazelbuild/bazel-gazelle/releases/download/v0.24.0/bazel-gazelle-v0.24.0.tar.gz",
    ],
)

# Load macros and repository rules.
load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")
load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies", "go_repository")

####
# Show casing the git_repository support bug
# Comment out the go_repository and uncomment the git_repository, then run bazel run //:gazelle
go_repository(
    name = "com_github_tigersoldier_gazelle_demo",
    importpath = "github.com/tigersoldier/gazelle-demo",
    sum = "h1:Mafq8JTThXQWLmd3GDDVwniPv90p0lTV5Iuc8KRFOoI=",
    version = "v0.0.0-20211206203318-4d00bfc2e984",
)

# git_repository(
#     name = "com_github_tigersoldier_gazelle_demo",
#     branch = "main",
#     remote = "ssh://git@github.com/tigersoldier/gazelle-demo",
# )

########
# Finalize Go dependency declaration

# Declare indirect dependencies and register toolchains.
go_rules_dependencies()

go_register_toolchains(version = "1.17.3")

gazelle_dependencies()
