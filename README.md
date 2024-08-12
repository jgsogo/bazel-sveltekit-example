# bazel-sveltekit-example
Bazel + Sveltekit

# my-app

The `my-app` application was created using

```
pnpm create svelte@latest my-app
```

# Working

The development server works:

```
bazel run //my-app:devserver
```

# Issues

 1. Why the `//my-app:sync` doesn't generate all the files (everything inside `.svelte-kit/types` is missing)

    ```
    bazel build //my-app:sync
    ```

 2. Tests are failing becuase SvelteKit cannot write in the sandbox:

    ```
    bazel test //my-app:vitest


    Error: EACCES: permission denied, open '.../sandbox/darwin-sandbox/1363/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/my-app/vitest_/vitest.runfiles/_main/my-app/.svelte-kit/tsconfig.json'
    ```
