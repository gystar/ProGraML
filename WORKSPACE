workspace(name = "programl")

# === Begin ProGraML dependencies ===
load("@programl//tools:bzl/deps.bzl", "programl_deps")

programl_deps()

# Boost.
load("@com_github_nelhage_rules_boost//:boost/boost.bzl", "boost_deps")

boost_deps()

# Python config. Needed by pybind11_bazel.
load("@programl//third_party/py:python_configure.bzl", programl_python_configure = "python_configure")

programl_python_configure(name = "local_config_python")

# LLVM.
load("@llvm//tools/bzl:deps.bzl", "llvm_deps")

llvm_deps()

# Bats.
load("@com_github_chriscummins_rules_bats//:bats.bzl", "bats_deps")

bats_deps()

# Python requirements.
load(
    "@rules_python//python:pip.bzl",
    "pip3_import",
    "pip_repositories",
)

pip_repositories()

pip3_import(
    name = "programl_requirements",
    timeout = 3600,
    requirements = "@programl//:programl/requirements.txt",
)

load(
    "@programl_requirements//:requirements.bzl",
    programl_pip_install = "pip_install",
)

programl_pip_install()

# Protobuf.
pip3_import(
    name = "protobuf_py_deps",
    timeout = 3600,
    requirements = "@build_stack_rules_proto//python/requirements:protobuf.txt",
)

load(
    "@protobuf_py_deps//:requirements.bzl",
    protobuf_pip_install = "pip_install",
)

protobuf_pip_install()

# Tensorflow.
load("@org_tensorflow//tensorflow:workspace.bzl", "tf_repositories")

tf_repositories()
# === End ProGraML dependencies ===

pip3_import(
    name = "tasks_requirements",
    timeout = 3600,
    requirements = "@programl//:tasks/requirements.txt",
)

load(
    "@tasks_requirements//:requirements.bzl",
    tasks_pip_install = "pip_install",
)

tasks_pip_install()

pip3_import(
    name = "tests_requirements",
    timeout = 3600,
    requirements = "@programl//:tests/requirements.txt",
)

load(
    "@tests_requirements//:requirements.bzl",
    tests_pip_install = "pip_install",
)

tests_pip_install()
