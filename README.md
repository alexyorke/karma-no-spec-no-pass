# karma-no-spec-no-pass
Fail tests which have no expectations defined. Compatible with Angular.

```
Spec 'my spec that does not have any expects() written' has no expectations; aborting tests.  
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! my-app@0.0.0 test: `ng test`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the my-app@0.0.0 test script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
```

## Why should I use this?

If a test doesn't have any expectations defined, then something might be wrong: the expects weren't triggered because the callback wasn't run, or another issue. This could occur because of flaky tests.

If you're trying to check if a service was called but it doesn't return anything, try using the `spyOn` expectation.

## How to use

In `karma.conf.js`, add `require('./karma-no-spec-no-pass')` to the end of the `plugins` array:

```
plugins: [
      require('karma-jasmine'),
      require('karma-chrome-launcher'),
      ...
      require('./karma-no-spec-no-pass')
    ],
```

Add `no-spec-no-pass` to the end of the `reporters` array:

```
reporters: [..., 'progress', 'no-spec-no-pass'],
```

Copy the file `karma-no-spec-no-pass.js` to the same directory that the file `karma.conf.js` is.
