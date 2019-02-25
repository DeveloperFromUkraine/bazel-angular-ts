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
  name = "io_bazel_skydoc",
  url = "https://github.com/bazelbuild/skydoc/archive/1cdb612e31448c2f6eb25b8aa67d406152275482.zip",
  strip_prefix = "skydoc-1cdb612e31448c2f6eb25b8aa67d406152275482",
  sha256 = "282ab93ea7477ad703b3e8108a274c21344c3b59ee4e5b1e6a89cdbe3ecbe68f",
)

http_archive(
  name = "bazel_skylib",
  url = "https://github.com/bazelbuild/bazel-skylib/archive/0.6.0.zip",
  strip_prefix = "bazel-skylib-0.6.0",
  sha256 = "54ee22e5b9f0dd2b42eb8a6c1878dee592cfe8eb33223a7dbbc583a383f6ee1a",
)

ANGULAR_VERSION = "7.1.3"
http_archive(
    name = "angular",
    strip_prefix = "angular-%s" % ANGULAR_VERSION,
    url = "https://github.com/angular/angular/archive/%s.zip" % ANGULAR_VERSION,
)

RXJS_VERSION = "6.3.3"
http_archive(
    name = "rxjs",
    strip_prefix = "package/src",
    url = "https://registry.npmjs.com/rxjs/-/rxjs-%s.tgz" % RXJS_VERSION,
)

RULES_SASS_VERSION = "1.15.2"
http_archive(
    name = "io_bazel_rules_sass",
    url = "https://github.com/bazelbuild/rules_sass/archive/%s.zip" % RULES_SASS_VERSION,
    strip_prefix = "rules_sass-%s" % RULES_SASS_VERSION,
)

load("@angular//packages/bazel:package.bzl", "rules_angular_dependencies")
rules_angular_dependencies()

load("@build_bazel_rules_typescript//:package.bzl", "rules_typescript_dependencies")
rules_typescript_dependencies()

load("@build_bazel_rules_nodejs//:defs.bzl", "npm_install")

npm_install(
  name = "npm",
  package_json = "//:package.json",
  package_lock_json="//:package-lock.json"
)

load("@build_bazel_rules_typescript//:defs.bzl", "ts_setup_workspace", "check_rules_typescript_version")
ts_setup_workspace()

#Angular workspace
load("@angular//:index.bzl", "ng_setup_workspace")
ng_setup_workspace()

load("@io_bazel_skydoc//skylark:skylark.bzl", "skydoc_repositories")
skydoc_repositories()
