# Snyk Lerna Failure demo

This repo demonstrates the issue reported in https://github.com/snyk/snyk/issues/289, where running `snyk test` via lerna on a sub-package with no dependencies results in a failure, where a preferred result would be simply to accept that there are no dependencies listed in `package.json` and move on.

To re-create the scenario after clone:

```
  $ npm install
  $ npm run bootstrap
  $ npm run snyk
```

`packages/subpkg` is a sub-package managed by lerna that does not have any `dependencies` or `devDependencies`. When lerna is used to run `snyk test` on this package, it reports:

```
> lerna exec 'snyk test --dev'

lerna notice cli v3.22.1
lerna info Executing command in 1 package: "snyk test --dev"
Missing node_modules folder: we can't test without dependencies.
Please run 'npm install' first.

lerna ERR! snyk test --dev exited 2 in 'subpkg'
```

This issue does go away when `npm install` is manually executed in `packages/subpkg`, which creates a minimal `package-lock.json`. Lerna's `bootstrap` command does not create this package-lock file. It seems to be a mismatch between Lerna's behavior when there are no dependencies (do not create a lockfile) and snyk's expectations (a lockfile always exists).

I defer to the snyk and lerna communities as to how to address this failure.

