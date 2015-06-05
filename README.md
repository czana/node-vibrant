# node-vibrant
Extract prominent colors from an image.

`node-vibrant` is a node.js port of [Vibrant.js](https://github.com/jariz/vibrant.js), which is a javascript port of the [awesome Palette class](https://developer.android.com/reference/android/support/v7/graphics/Palette.html) in the Android support library.

## Install

```bash
$ npm install node-vibrant
```

## Usage

```coffee
Vibrant = require('node-vibrant')

v = new Vibrant('path/to/image', opts)
v.getSwatches (err, swatches) ->
  console.log(swatches)
```

## References

### `Vibrant.constructor(imagePath, opts)`

Name | Type | Description
---- | ---- | --------------
`imagePath` | string | Path to image file
`opts` | object | Options (optional)

#### `opts`

Field | Default | Description
----- | ------- | -----------
`colorCount` | `64` | amount of colors in initial palette from which the swatches will be generated
`quality` | `5` | 1 is highest, but takes way more processing



### `Vibrant.getSwatches(cb)`

Name | Type | Description
---- | ---- | --------------
`cb` | function | callback function

#### `cb(err, swatches)`

Name | Type | Description
---- | ---- | --------------
`err` | object | Error (if thrown)
`swatches` | object | Resulting swatches

## Benchmark

Run `gulp benchmark` to see how `opts` value affects performance.

```
[12:53:52] Running suite node-vibrant colorCount benchmark (quality = 5)
[12:53:58]    Color count: 2 x 9.83 ops/sec ±2.67% (52 runs sampled)
[12:54:04]    Color count: 4 x 9.52 ops/sec ±1.02% (50 runs sampled)
[12:54:10]    Color count: 8 x 9.01 ops/sec ±1.39% (47 runs sampled)
[12:54:16]    Color count: 16 x 8.29 ops/sec ±0.95% (44 runs sampled)
[12:54:22]    Color count: 32 x 7.95 ops/sec ±0.85% (43 runs sampled)
[12:54:28]    Color count: 64 x 7.23 ops/sec ±2.17% (39 runs sampled)
[12:54:33]    Color count: 128 x 7.42 ops/sec ±1.00% (40 runs sampled)
[12:54:39]    Color count: 256 x 6.36 ops/sec ±2.54% (35 runs sampled)
[12:54:39] Fastest test is Color count: 2 at 1.03x faster than Color count: 4
[12:54:39] Running suite node-vibrant quality benchmark (colorCount = 64)
[12:54:46]    Quality: 1 x 3.11 ops/sec ±5.63% (20 runs sampled)
[12:54:53]    Quality: 2 x 3.53 ops/sec ±3.11% (22 runs sampled)
[12:54:59]    Quality: 3 x 3.95 ops/sec ±1.98% (24 runs sampled)
[12:55:05]    Quality: 4 x 4.29 ops/sec ±1.24% (26 runs sampled)
[12:55:12]    Quality: 5 x 4.44 ops/sec ±0.97% (26 runs sampled)
[12:55:18]    Quality: 6 x 4.55 ops/sec ±1.14% (27 runs sampled)
[12:55:24]    Quality: 7 x 4.60 ops/sec ±0.77% (27 runs sampled)
[12:55:30]    Quality: 8 x 4.59 ops/sec ±1.41% (27 runs sampled)
[12:55:30] Fastest tests are Quality: 7,Quality: 8 at 1.00x faster than Quality: 8
[12:55:30] Finished 'benchmark' after 1.63 min
```