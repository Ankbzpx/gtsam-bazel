workspace(
    name = "gtsam_bazel",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# Copied from: https://github.com/ceres-solver/ceres-solver/blob/master/WORKSPACE
# External dependency: Eigen; has no Bazel build.
http_archive(
    name = "com_gitlab_libeigen_eigen",
    sha256 = "3d6c79191c03e1b35cc14d6a8caee9284455974ee86f22941c5a82a379384335",
    strip_prefix = "eigen-3.3.8",
    urls = [
        "https://gitlab.com/libeigen/eigen/-/archive/3.3.8/eigen-3.3.8.zip",
    ],
    build_file_content =
"""
# TODO(keir): Replace this with a better version, like from TensorFlow.
# See https://github.com/ceres-solver/ceres-solver/issues/337.
cc_library(
    name = 'eigen',
    srcs = [],
    includes = ['.'],
    hdrs = glob(['Eigen/**']),
    visibility = ['//visibility:public'],
)
"""
)

git_repository(
    name = "com_github_nelhage_rules_boost",
    commit = "1e3a69bf2d5cd10c34b74f066054cd335d033d71",
    remote = "https://github.com/nelhage/rules_boost",
    shallow_since = "1591047380 -0700",
)

load("@com_github_nelhage_rules_boost//:boost/boost.bzl", "boost_deps")
boost_deps()

# GTSAM - GTSAM is a library of C++ classes that implement smoothing and mapping (SAM) in robotics and vision, 
# using factor graphs and Bayes networks as the underlying computing paradigm rather than sparse matrices.
http_archive(
    name = "com_github_borglab_gtsam",
    patch_args = [
        "-p1",
    ],
    patches = [
        "@//third_party:com_github_borglab_gtsam_fixes.diff",
    ],
    sha256 = "eaa561749edf7a2d402981828253e28aed6c717dae35738301c5ab23e2595f25",
    strip_prefix = "gtsam-4.0.3",
    urls = [
        "https://github.com/borglab/gtsam/archive/4.0.3.tar.gz",
    ],
)