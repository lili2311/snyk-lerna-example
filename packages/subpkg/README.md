# Snyk Lerna Failure Sub-Package

This is a sub-package managed by lerna that does not have any `dependencies` or `devDependencies`. When lerna is used to run `snyk test` on this package, it reports: 

```
> lerna exec 'snyk test --dev'

lerna notice cli v3.22.1
lerna info Executing command in 1 package: "snyk test --dev"
Missing node_modules folder: we can't test without dependencies.
Please run 'npm install' first.

lerna ERR! snyk test --dev exited 2 in 'subpkg'
```

