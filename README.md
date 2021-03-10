# gtsam-bazel
Build gtsam with bazel, tested on Manjaro

## Test
Run official [ISAM2](https://github.com/borglab/gtsam/blob/develop/examples/VisualISAM2Example.cpp) example with
```
bazel run @com_github_borglab_gtsam//:visual-isam2-example
```

## Usage

Add `@com_github_borglab_gtsam//:libgtsam` to `cc_binary` or `cc_library` dependency

For example: 
```
cc_binary(
    name = "gtsam-demo",
    srcs = ["gtsam-demo.cc"],
    deps = [
        "@com_github_borglab_gtsam//:libgtsam",
    ],
)
```
