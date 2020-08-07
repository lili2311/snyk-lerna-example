# Snyk Lerna Failure demo

This repo demonstrates the issue reported in https://github.com/snyk/snyk/issues/289, where running `snyk test` via lerna on a sub-package with no dependencies results in a failure, where a preferred result would be simply to accept that there are no dependencies listed in `package.json` and move on.

To re-create the scenario after clone:

```
  $ npm install
  $ npm run snyk
```

