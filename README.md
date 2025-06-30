# Suspend Resource

[Ready resource](https://github.com/holepunchto/ready-resource) with resume/suspend functionality.

```
npm install suspend-resource
```

## Usage

``` js
const SuspendResource = require('suspend-resource')

class Thing extends SuspendResource {
  constructor () {
    super()
  }

  async _open () {
    // open the resource
  }

  async _close () {
    // close the resource
  }

  async _suspend() {
    // suspend the resource (only implement if suspend/resume is required)
  }

  async _resume_() {
    // resume the resource (only implement if suspend/resume is required)
  }
}

const r = new Thing()

await r.ready() // calls _open once
await r.ready() // noop

await r.suspend() // calls _suspend once
await r.suspend() // noop

await r.resume() // calls _resume once
await r.resume() // noop

await Promise.all([r.suspend(), r.resume()]) // ends up resumed, since resume is the last method to be called 

await r.close()
```
