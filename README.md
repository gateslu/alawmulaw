# alawmulaw
Copyright (c) 2018 Rafael da Silva Rocha.  
https://github.com/rochars/alawmulaw

[![NPM version](https://img.shields.io/npm/v/alawmulaw.svg?style=for-the-badge)](https://www.npmjs.com/package/alawmulaw) [![Docs](https://img.shields.io/badge/docs-online-blue.svg?style=for-the-badge)](https://rochars.github.io/alawmulaw/index.html)  
[![Codecov](https://img.shields.io/codecov/c/github/rochars/alawmulaw.svg?style=flat-square)](https://codecov.io/gh/rochars/alawmulaw) [![Unix Build](https://img.shields.io/travis/rochars/alawmulaw.svg?style=flat-square)](https://travis-ci.org/rochars/alawmulaw) [![Windows Build](https://img.shields.io/appveyor/ci/rochars/alawmulaw.svg?style=flat-square&logo=appveyor)](https://ci.appveyor.com/project/rochars/alawmulaw) [![Scrutinizer](https://img.shields.io/scrutinizer/g/rochars/alawmulaw.svg?style=flat-square&logo=scrutinizer)](https://scrutinizer-ci.com/g/rochars/alawmulaw/)

A-Law and mu-Law codecs in JavaScript.

## Install
```
npm install alawmulaw
```

## Use

### ES6
import WaveFile from **alawmulaw.js**:
```javascript
import alawmulaw from 'alawmulaw.js';
let aLawSamples = alawmulaw.alaw.encode(pcmSamples);
```

### Node
```javascript
const alawmulaw = require("alawmulaw");

// Encode all the samples in a file
// Only 16-bit samples are supported
let aLawSamples = alawmulaw.alaw.encode(pcmSamples);
```

### Browser
Use the compiled file in the */dist* folder:
```html
<script src="alawmulaw.min.js"></script>
<script>
    // A-Law
    samples = alawmulaw.alaw.encode(samples);
    samples = alawmulaw.alaw.decode(samples);
    sample = alawmulaw.alaw.encodeSample(sample);
    sample = alawmulaw.alaw.decodeSample(sample);

    // mu-Law
    samples = alawmulaw.mulaw.encode(samples);
    samples = alawmulaw.mulaw.decode(samples);
    sample = alawmulaw.mulaw.encodeSample(sample);
    sample = alawmulaw.mulaw.decodeSample(sample);
</script>
```

Or get it from the [jsDelivr](https://www.jsdelivr.com) CDN:
```html
<script src="https://cdn.jsdelivr.net/npm/alawmulaw@4"></script>
```

Or get it from [unpkg](https://www.unpkg.com):
```html
<script src="https://unpkg.com/alawmulaw@4"></script>
```

Or as a ES6 module in modern browsers from [jspm](https://jspm.io):
```html
<script type="module">
  import alawmulaw from 'https://dev.jspm.io/alawmulaw';
  // ...
</script>
```

## Encode / Decode:

### A-Law
Full files:
```javascript
const alaw = require("alawmulaw").alaw;

// Encode all the samples in a file
// Only 16-bit samples are supported
aLawSamples = alaw.encode(pcmSamples);

// Decompressing all the samples in a file
pcmSamples = alaw.decode(aLawSamples);
```

Sample by sample:
```javascript
const alaw = require("alawmulaw").alaw;

// Encoding
aLawSample = alaw.encodeSample(pcmSample);

// Decoding
pcmSample = alaw.decodeSample(aLawSample);
```

### mu-Law
Full files:
```javascript
const mulaw = require("alawmulaw").mulaw;

// Encode all the samples in a file
// Only 16-bit samples are supported
muLawSamples = mulaw.encode(pcmSamples);

// Decode all the samples in a file
pcmSamples = mulaw.decode(muLawSamples);
```

Sample by sample:
```javascript
const mulaw = require("alawmulaw").mulaw;

// Encoding
muLawSample = mulaw.encodeSample(pcmSample);

// Decoding
pcmSample = mulaw.decodeSample(muLawSample);
```

## API

### alawmulaw.alaw
```javascript
/**
 * Encode a 16-bit linear PCM sample as 8-bit A-Law.
 * @param {number} sample A 16-bit linear PCM sample
 * @return {number}
 */
function encodeSample(sample) {}

/**
 * Decode a 8-bit A-Law sample as 16-bit linear PCM.
 * @param {number} aLawSample The 8-bit A-Law sample
 * @return {number}
 */
function decodeSample(aLawSample) {}

/**
 * Encode 16-bit linear PCM samples into 8-bit A-Law samples.
 * @param {!Array<number>} samples A array of 16-bit PCM samples.
 * @return {!Array<number>}
 */
function encode(samples) {}

/**
 * Decode 8-bit A-Law samples into 16-bit linear PCM samples.
 * @param {!Array<number>} samples A array of 8-bit A-Law samples.
 * @return {!Array<number>}
 */
function decode(samples) {}
```

### alawmulaw.mulaw
```javascript
/**
 * Encode a 16-bit linear PCM sample as 8-bit mu-Law.
 * @param {number} pcmSample A 16-bit sample
 * @return {number}
 */
function encodeSample(pcmSample) {}

/**
 * Decode a 8-bit mu-Law sample as 16-bit linear PCM.
 * @param {number} muLawSample The 8-bit mu-Law sample
 * @return {number}
 */
function decodeSample(muLawSample) {}

/**
 * Encode 16-bit linear PCM samples into 8-bit mu-Law samples.
 * @param {!Array<number>} samples A array of 16-bit linear PCM samples.
 * @return {!Array<number>}
 */
function encode(samples) {}

/**
 * Decode 8-bit mu-Law samples into 16-bit linear PCM samples.
 * @param {!Array<number>} samples A array of 8-bit mu-Law samples.
 * @return {!Array<number>}
 */
function decode(samples) {}
```

## Distribution
This library is a ES6 module also distributed as a CommonJS module, UMD and a compiled script for browsers.

- The **CommonJS** is the one used by Node. It is served in the "main" field of package.json
- The **UMD** module is compatible with Node, AMD and browsers. It is served in the "browser" field.
- The **compiled dist** is browser-only and should be the one served by CDNs.
- The **ES6** dist is **alawmulaw.js**, served as "module" in package.json

You may load both **alawmulaw.umd.js** and **alawmulaw.min.js** in the browser with ```<script>``` tags.

## References
https://github.com/torvalds/linux/blob/master/sound/core/oss/mulaw.c  
https://github.com/deftio/companders  
http://dystopiancode.blogspot.com.br/2012/02/pcm-law-and-u-law-companding-algorithms.html

### LICENSE
Copyright (c) 2018 Rafael da Silva Rocha.

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
