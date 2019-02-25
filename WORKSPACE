# The WORKSPACE file tells Bazel that this directory is a "workspace", which is like a project root.
# The content of this file specifies all the external dependencies Bazel needs to perform a build.

workspace(name = "ngx_bootstrap_new_bazel")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
  name = "build_bazel_rules_nodejs",
  remote = "git@github.com:DeveloperFromUkraine/rules_nodejs.git",
  commit = "peer-deps-optional"
)

http_archive(
    name = "io_bazel_rules_sass",
    sha256 = "dbe9fb97d5a7833b2a733eebc78c9c1e3880f676ac8af16e58ccf2139cbcad03",
    strip_prefix = "rules_sass-1.11.0",
    url = "https://github.com/bazelbuild/rules_sass/archive/1.11.0.zip",
)

load("@build_bazel_rules_nodejs//:defs.bzl", "npm_install")

npm_install(
  name = "npm",
  package_json = "//:package.json",
#  yarn_lock = "//:yarn.lock",
  package_lock_json="//:package-lock.json"
)

load("@npm//bazel/typescript:defs.bzl", "ts_setup_workspace")
ts_setup_workspace()

load("@npm//angular/bazel:index.bzl", "ng_setup_workspace")
ng_setup_workspace()

