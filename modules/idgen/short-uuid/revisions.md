# Revisions

# v2.3.2

2.3.2 merges a TypeScript definition from [alexturek](https://github.com/alexturek).

# v2.3.1

2.3.1 merges the version history of the 2.1.x branch updates.

# v2.3.0

2.3.0 moves Snyk to a dev dependency.

# v2.2.0 - DEPRECATED

2.2.0 updates dev dependencies and adds Snyk vulnerability monitoring and patching.

# v2.1.4

2.1.0 adds Browserify config to support client-side use as proposed by [voronianski](https://github.com/voronianski).
2.1.1 includes compiled browser-ready files in the npm package for convenience. The library is exposed as `ShortUUID`.
2.1.2 switches to the modular `uuid` library.
2.1.3 fixes a bad npm package for 2.1.1 which included Snyk incorrectly.
2.1.4 corrects documentation of 2.1.2 from unpublished to deprecated.

## v2.1.2 Deprecated

An incorrect package.json was packaged in v2.1.2, causing Snyk to be listed as a dependency. 
This was introduced in v2.2.0.

# v2.1.3

2.1.3 corrects a bad package.json in the 2.1.2 npm package.

# v2.1.2 - DEPRECATED

2.1.2 changes to `uuid` 3.0.0 and uses only the `uuid/v4` module.

# v2.1.2

2.1.2 changes to `uuid` 3.0.0 and uses only the `uuid/v4` module.

# v2.1.1

2.1.1 includes the compiled Browserify files in the npm package for convenience.

# v2.1.0

2.1 provides [Browserify](http://browserify.org) support as proposed by [voronianski](https://github.com/voronianski),
exposing the interface at `ShortUUID`.

# v2.0.0

2.0 is a major rework to make the library more capable and useful. It now provides RFC4122 v4-compliant UUIDs,
thanks to [`node-uuid`](https://github.com/broofa/node-uuid).

```javascript
var short = require('short-uuid');
var translator = short(); // Defaults to flickrBase58
var decimalTranslator = short("0123456789"); // Provide a specific alphabet for translation
var cookieTranslator = short(short.constants.cookieBase90); // Use a constant for translation

// Generate a shortened v4 UUID
translator.new();

// Generate plain UUIDs
short.uuid(); // From the constructor without creating a translator
translator.uuid(); // Each translator provides the uuid.v4() function

// Translate UUIDs
translator.toUUID(shortId);
translator.fromUUID(regularUUID);

// See the alphabet used by a translator
translator.alphabet

// View the constants
short.constants.flickrBase58;
short.constants.cookieBase90;

```

# v1.0.0

Translate standard UUIDs into shorter formats and back.

`require('short-uuid')` returns an object with a "new" function that takes a base as a parameter and returns to/from functions:

    {
      fromUUID: function(){..},
      toUUID: function(){..}
      fromHex: function(){..},
      toHex: function(){..},
    }

The 'UUID' Functions handle the dashes and left-filled zeros needed for proper UUID support. The 'Hex' functions provide the translation functions from `any-base`.

The object also incldues a `constants` object, with base58 and base90 sets.
The base58 set `flickrBase58` originates with Flickr and reduces human transcription errors.
The base90 set `cookieBase90` is the set of allowable characters in a cookie value, and is intended to provide the shortest storage of UUIDs in a browser cookie.

Finally, the Base58 translator is automatically generated and included as `b58` for convenience.