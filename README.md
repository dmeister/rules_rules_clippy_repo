`bazel test //...` fails with

```
INFO: Analyzed target //hello_world:hello_world (1 packages loaded, 2 targets configured).
INFO: Found 1 target and 0 test targets...
ERROR: XXXX/hello_world/BUILD:7:12: Clippy hello_world/hello_world.clippy.ok failed: (Exit 1): process_wrapper failed: error executing command (from target //hello_world:hello_world) bazel-out/k8-opt-exec-2B5CBBC6/bin/external/rules_rust/util/process_wrapper/process_wrapper --arg-file bazel-out/k8-fastbuild/bin/external/crate_index__slab-0.4.9/slab_build_script.linksearchpaths ... (remaining 87 arguments skipped)

Use --sandbox_debug to see verbose messages from the sandbox and retain the sandbox build root for debugging
error: Option 'sysroot' given more than once

Aspect @rules_rust//rust/private:clippy.bzl%rust_clippy_aspect of //hello_world:hello_world failed to build
Use --verbose_failures to see the command lines of failed build steps.
INFO: Elapsed time: 2.180s, Critical Path: 0.10s
INFO: 3 processes: 3 internal.
FAILED: Build did NOT complete successfully
ERROR: No test targets were found, yet testing was requested
```
