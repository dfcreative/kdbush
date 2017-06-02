## kdgrass [![Build Status](https://travis-ci.org/dfcreative/kdgrass.svg?branch=master)](https://travis-ci.org/dfcreative/kdgrass) [![Simply Awesome](https://img.shields.io/badge/simply-awesome-brightgreen.svg)](https://github.com/dfcreative/projects)

A very fast static spatial index for 2D points based on a flat KD-tree, with optimized API, compared to [KDBush](https://github.com/mourner/kdbush).

```js
var index = kdgrass(points);              // make an index
var ids1 = index.range(10, 10, 20, 20);  // bbox search - minX, minY, maxX, maxY
var ids2 = index.within(10, 10, 5);      // radius search - x, y, radius
```

## API

#### kdgrass(points, nodeSize?)

Creates an index from the given points.

- `points`: Input array of points in [x, y, x, y, ...] form.
- `nodeSize`: Size of the KD-tree node, `64` by default. Higher means faster indexing but slower search, and vise versa.

```js
var index = kdgrass(points, 64);
```

#### range(minX, minY, maxX, maxY)

Finds all items within the given bounding box and returns an array of indices that refer to the items in the original `points` input array.

```js
var results = index.range(10, 10, 20, 20).map((id) => points[id]);
```

#### within(x, y, radius)

Finds all items within a given radius from the query point and returns an array of indices.

```js
var results = index.within(10, 10, 5).map((id) => points[id]);
```

## See also

* [kdbush](https://github.com/mourner/kdbush) − initial implementation with more verbose API.
* [rbush](https://github.com/mourner/rbush) — even more verbose implementation with dynamic insertion/removal API.
