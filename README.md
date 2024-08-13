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

We can also run tests

```
bazel test //my-app:vitest
```
