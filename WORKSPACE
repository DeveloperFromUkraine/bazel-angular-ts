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

#http_archive(
#    name = "io_bazel_rules_sass",
#    sha256 = "dbe9fb97d5a7833b2a733eebc78c9c1e3880f676ac8af16e58ccf2139cbcad03",
#    strip_prefix = "rules_sass-1.11.0",
#    url = "https://github.com/bazelbuild/rules_sass/archive/1.11.0.zip",
#)
#
#load("@build_bazel_rules_nodejs//:defs.bzl", "npm_install")
#
#npm_install(
#  name = "npm",
#  package_json = "//:package.json",
##  yarn_lock = "//:yarn.lock",
#  package_lock_json="//:package-lock.json"
#)
#
#load("@npm//bazel/typescript:defs.bzl", "ts_setup_workspace")
#ts_setup_workspace()
#
#load("@npm//angular/bazel:index.bzl", "ng_setup_workspace")
#ng_setup_workspace()
#
#load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Fetch rules_nodejs so we can install our npm dependencies
#http_archive(
#    name = "build_bazel_rules_nodejs",
#    sha256 = "86ea92217dfd4a84e1e335cc07dfd942b12899796b080492546b947f12c5ab77",
#    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/0.26.0-beta.0/rules_nodejs-0.26.0-beta.0.tar.gz"],
#)

# Fetch sass rules for compiling sass files
http_archive(
    name = "io_bazel_rules_sass",
    sha256 = "dbe9fb97d5a7833b2a733eebc78c9c1e3880f676ac8af16e58ccf2139cbcad03",
    strip_prefix = "rules_sass-1.11.0",
    url = "https://github.com/bazelbuild/rules_sass/archive/1.11.0.zip",
)

# Check the bazel version and download npm dependencies
load("@build_bazel_rules_nodejs//:defs.bzl", "yarn_install")

# Install our npm dependencies into @npm
yarn_install(
    name = "npm",
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
    data = ["@angular//:LICENSE"]
)

# Install all bazel dependencies of our npm packages
load("@npm//:install_bazel_dependencies.bzl", "install_bazel_dependencies")
install_bazel_dependencies()

# Setup the rules_typescript tooolchain
load("@npm_bazel_typescript//:defs.bzl", "ts_setup_workspace")
ts_setup_workspace()

# Setup the rules_sass toolchain
load("@io_bazel_rules_sass//sass:sass_repositories.bzl", "sass_repositories")
sass_repositories()

load("@npm_angular_bazel//:index.bzl", "ng_setup_workspace")
ng_setup_workspace()
