<!--

@license Apache-2.0

Copyright (c) 2020 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# dmap

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> C API for registering a Node-API module exporting a strided array interface for applying a unary callback to a double-precision floating-point strided input array and assigning results to a double-precision floating-point strided output array.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/strided-napi-dmap
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm` branch][esm-url].
-   If you are using Deno, visit the [`deno` branch][deno-url].
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd` branch][umd-url].

</section>

<section class="usage">

## Usage

```javascript
var headerDir = require( '@stdlib/strided-napi-dmap' );
```

#### headerDir

Absolute file path for the directory containing header files for C APIs.

```javascript
var dir = headerDir;
// returns <string>
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

```javascript
var headerDir = require( '@stdlib/strided-napi-dmap' );

console.log( headerDir );
// => <string>
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/strided/napi/dmap.h"
```

#### stdlib_strided_napi_dmap( env, info, fcn )

Invokes a strided array interface which applies a unary callback to a double-precision floating-point strided input array and assigns results to a double-precision floating-point strided output array.

```c
#include <node_api.h>

// ...

static double identity( const double x ) {
    return x;
}

// ...

/**
* Receives JavaScript callback invocation data.
*
* @param env    environment under which the function is invoked
* @param info   callback data
* @return       Node-API value
*/
napi_value addon( napi_env env, napi_callback_info info ) {
    stdlib_strided_napi_dmap( env, info, identity );
    return NULL;
}

// ...
```

The function accepts the following arguments:

-   **env**: `[in] napi_env` environment under which the function is invoked.
-   **info**: `[in] napi_callback_info` callback data.
-   **fcn**: `[in] double (*fcn)( double )` unary callback.

```c
void stdlib_strided_napi_dmap( napi_env env, napi_callback_info info, double (*fcn)( double ) );
```

#### STDLIB_STRIDED_NAPI_MODULE_DMAP( clbk )

Macro for registering a Node-API module exporting a strided array interface for applying a unary callback to a double-precision floating-point strided input array and assigning results to a double-precision floating-point strided output array.

```c
static double scale( const double x ) {
    return x * 10.0;
}

// ...

// Register a Node-API module:
STDLIB_STRIDED_NAPI_MODULE_DMAP( scale );
```

The macro expects the following arguments:

-   **clbk**: `double (*fcn)( double )` unary callback.

When used, this macro should be used **instead of** `NAPI_MODULE`. The macro includes `NAPI_MODULE`, thus ensuring Node-API module registration.

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

### Notes

-   The function expects that the callback `info` argument provides access to the following JavaScript arguments:

    -   **N**: number of indexed elements.
    -   **X**: input [`Float64Array`][@stdlib/array/float64].
    -   **strideX**: `X` stride length.
    -   **Y**: destination [`Float64Array`][@stdlib/array/float64].
    -   **strideY**: `Y` stride length.

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2022. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/strided-napi-dmap.svg
[npm-url]: https://npmjs.org/package/@stdlib/strided-napi-dmap

[test-image]: https://github.com/stdlib-js/strided-napi-dmap/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/strided-napi-dmap/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/strided-napi-dmap/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/strided-napi-dmap?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/strided-napi-dmap.svg
[dependencies-url]: https://david-dm.org/stdlib-js/strided-napi-dmap/main

-->

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/strided-napi-dmap/tree/deno
[umd-url]: https://github.com/stdlib-js/strided-napi-dmap/tree/umd
[esm-url]: https://github.com/stdlib-js/strided-napi-dmap/tree/esm

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/strided-napi-dmap/main/LICENSE

[@stdlib/array/float64]: https://github.com/stdlib-js/array-float64

</section>

<!-- /.links -->
