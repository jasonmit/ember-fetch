# Ember-fetch [![Build Status](https://travis-ci.org/stefanpenner/ember-fetch.svg?branch=master)](https://travis-ci.org/stefanpenner/ember-fetch)

HTML5 [fetch](https://fetch.spec.whatwg.org) polyfill from [github](https://github.com/github/fetch) wrapped and bundled for ember-cli users

* [intro to fetch](http://updates.html5rocks.com/2015/03/introduction-to-fetch)
* [spec](https://fetch.spec.whatwg.org)
* [usage](https://github.com/github/fetch#usage)
* [origin repo](https://github.com/github/fetch)

## Installation

* `ember install:addon ember-fetch`

## Usage

```js
import fetch from 'fetch';
import Ember from 'ember';

export default Ember.Route.extend({
  model() {
    return fetch('/my-cool-end-point.json').then(function(response) {
      return response.json();
    });
  }
});
```

further docs: https://github.com/github/fetch

### Browser Support

* evergreen / IE9+ / Safari 6.1+ https://github.com/github/fetch#browser-support


### does this replace ic-ajax?

* ideally yes, but only if you cater to IE9+
* for basic drop-in compat `import ajax from 'fetch/ajax'`

### What about all the run-loop and promise mixing details?

* taken care of for you

### why is this wrapper needed?

* original emits a global
* original requires a Promise polyfil (ember users have RSVP)
* original isn't Ember run-loop aware

### Won't this wrapper get out-of-sync?

* we actually don't bundle github/fetch rather we merely wrap/transform what
  comes from `node_modules`, so we should be resilient to changes assuming
  semver from the fetch module

