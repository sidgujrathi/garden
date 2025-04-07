---
layout: post
title:  "Standard Library for JavaScript Runtimes (James Snell Talk)"
date:   2023-10-18
categories: ["Today I Learned"]
---
#### October 18, 2023

Watched the [talk](https://portal.gitnation.org/contents/towards-a-standard-library-for-javascript-runtimes) by Towards a Standard Library for JavaScript Runtimes by James Snell

- I found the talk very interesting, what James proposed is to have a new collaborative open-source effort which should be preferably driven jointly by contributors to NodeJS, Deno and other JS runtimes to develop a library of common APIs independent of runtimes
-  So what is the problem today, we have different runtimes and each runtime has its own set of APIs, so if you are using NodeJS and you want to use some APIs which are not available in NodeJS but available in Deno, then you have to use some third party library which will provide you the same functionality. For example, creating base64 from string, you can do that by any of the following
``` javascript
	// NodeJS
    const base64 = Buffer.from('Hello World').toString('base64');
    // Browser
    const base64 = btoa('Hello World');
    // Deno
    import {encode} from "https://deno.land/std/encoding/base64.ts";
    encode('Hello World');
    // npm package
    import {encode} from "base64";
    encode('Hello World');
```
- If you observe above code, you have multiple ways to do same thing in your own runtime, even we have packages which you can use to do same thing, why? Why we can't have a single standard library which can be used across all runtimes, so that we don't have to worry about the APIs and we can focus on our business logic.
