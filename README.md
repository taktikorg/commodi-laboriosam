# @taktikorg/commodi-laboriosam <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Define a data property on an object. Will fall back to assignment in an engine without descriptors.

The three `non*` argument can also be passed `null`, which will use the existing state if available.

The `loose` argument will mean that if you attempt to set a non-normal data property, in an environment without descriptor support, it will fall back to normal assignment.

## Usage

```javascript
var defineDataProperty = require('@taktikorg/commodi-laboriosam');
var assert = require('assert');

var obj = {};
defineDataProperty(obj, 'key', 'value');
defineDataProperty(
	obj,
	'key2',
	'value',
	true, // nonEnumerable, optional
	false, // nonWritable, optional
	true, // nonConfigurable, optional
	false // loose, optional
);

assert.deepEqual(
	Object.getOwnPropertyDescriptors(obj),
	{
		key: {
			configurable: true,
			enumerable: true,
			value: 'value',
			writable: true,
		},
		key2: {
			configurable: false,
			enumerable: false,
			value: 'value',
			writable: true,
		},
	}
);
```

[package-url]: https://npmjs.org/package/@taktikorg/commodi-laboriosam
[npm-version-svg]: https://versionbadg.es/ljharb/@taktikorg/commodi-laboriosam.svg
[deps-svg]: https://david-dm.org/ljharb/@taktikorg/commodi-laboriosam.svg
[deps-url]: https://david-dm.org/ljharb/@taktikorg/commodi-laboriosam
[dev-deps-svg]: https://david-dm.org/ljharb/@taktikorg/commodi-laboriosam/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/@taktikorg/commodi-laboriosam#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@taktikorg/commodi-laboriosam.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@taktikorg/commodi-laboriosam.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@taktikorg/commodi-laboriosam.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@taktikorg/commodi-laboriosam
[codecov-image]: https://codecov.io/gh/ljharb/@taktikorg/commodi-laboriosam/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ljharb/@taktikorg/commodi-laboriosam/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ljharb/@taktikorg/commodi-laboriosam
[actions-url]: https://github.com/taktikorg/commodi-laboriosam/actions
