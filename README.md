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

 1. Why the `//my-app:sync` doesn't generate all the files? Everything inside `.svelte-kit/types` is missing.

    ```
    bazel build //my-app:sync
    ```

 2. Tests are failing becuase SvelteKit cannot write in the sandbox:

    ```
    bazel test //my-app:vitest


    ⎯⎯⎯⎯⎯⎯⎯ Startup Error ⎯⎯⎯⎯⎯⎯⎯⎯
    Error: EACCES: permission denied, open '/private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/sandbox/darwin-sandbox/1/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/my-app/vitest_/vitest.runfiles/_main/my-app/.svelte-kit/tsconfig.json'
        at Object.openSync (node:fs:596:3)
        at Object.writeFileSync (node:fs:2322:35)
        at write (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/node_modules/.aspect_rules_js/@sveltejs+kit@2.0.0_2036152551/node_modules/@sveltejs/kit/src/core/sync/utils.js:26:5)
        at write_if_changed (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/node_modules/.aspect_rules_js/@sveltejs+kit@2.0.0_2036152551/node_modules/@sveltejs/kit/src/core/sync/utils.js:15:3)
        at write_tsconfig (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/node_modules/.aspect_rules_js/@sveltejs+kit@2.0.0_2036152551/node_modules/@sveltejs/kit/src/core/sync/write_tsconfig.js:46:2)
        at Module.init (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/node_modules/.aspect_rules_js/@sveltejs+kit@2.0.0_2036152551/node_modules/@sveltejs/kit/src/core/sync/sync.js:17:2)
        at dev (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/node_modules/.aspect_rules_js/@sveltejs+kit@2.0.0_2036152551/node_modules/@sveltejs/kit/src/exports/vite/dev/index.js:41:7)
        at configureServer (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/node_modules/.aspect_rules_js/@sveltejs+kit@2.0.0_2036152551/node_modules/@sveltejs/kit/src/exports/vite/index.js:621:17)
        at _createServer (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/sandbox/darwin-sandbox/1/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/my-app/vitest_/vitest.runfiles/_main/node_modules/.aspect_rules_js/vite@5.0.3/node_modules/vite/dist/node/chunks/dep-vyqc0_aB.js:59738:30)
        at async createViteServer (file:///private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/sandbox/darwin-sandbox/1/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/my-app/vitest_/vitest.runfiles/_main/node_modules/.aspect_rules_js/vitest@2.0.0/node_modules/vitest/dist/vendor/cli-api.BT4NJtxX.js:13754:18) {
    errno: -13,
    syscall: 'open',
    code: 'EACCES',
    path: '/private/var/tmp/_bazel_user/c15c176709cbf9e356528b7611105a10/sandbox/darwin-sandbox/1/execroot/_main/bazel-out/darwin_x86_64-fastbuild/bin/my-app/vitest_/vitest.runfiles/_main/my-app/.svelte-kit/tsconfig.json'
    }
    ```
