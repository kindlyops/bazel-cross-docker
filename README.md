# Test case for https://github.com/bazelbuild/bazel-watcher/issues/245

    bazel run //:image
    docker ps
    CTRL-C
    docker ps # observe that the docker image process is gone


    ibazel run //:image
    docker ps

make an edit to a file like BUILD.bazel (just adding a comment), save
see the build rerun

    docker ps # observe that the first image process did not get cleaned up
    CTRL-C twice
    docker ps # observe that both docker images are still running

use docker kill to clean up manually

## other debugging notes

bazel run -c dbg //:image -- --norun

docker inspect bazel:image

docker run -ti --rm --entrypoint=sh bazel:image

bazel run //:image