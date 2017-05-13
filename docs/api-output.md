<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [toFile](#tofile)
-   [toBuffer](#tobuffer)
-   [withMetadata](#withmetadata)
-   [jpeg](#jpeg)
-   [png](#png)
-   [webp](#webp)
-   [tiff](#tiff)
-   [raw](#raw)
-   [toFormat](#toformat)
-   [tile](#tile)

## toFile

Write output image data to a file.

If an explicit output format is not selected, it will be inferred from the extension,
with JPEG, PNG, WebP, TIFF, DZI, and libvips' V format supported.
Note that raw pixel data is only supported for buffer output.

A Promises/A+ promise is returned when `callback` is not provided.

**Parameters**

-   `fileOut` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** the path to write the image data to.
-   `callback` **[Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)?** called on completion with two arguments `(err, info)`.
    `info` contains the output image `format`, `size` (bytes), `width`, `height`,
    `channels` and `premultiplied` (indicating if premultiplication was used).


-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** Invalid parameters

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)>** when no callback is provided

## toBuffer

Write output to a Buffer.
JPEG, PNG, WebP, TIFF and RAW output are supported.
By default, the format will match the input image, except GIF and SVG input which become PNG output.

`callback`, if present, gets three arguments `(err, data, info)` where:

-   `err` is an error, if any.
-   `data` is the output image data.
-   `info` contains the output image `format`, `size` (bytes), `width`, `height`,
    `channels` and `premultiplied` (indicating if premultiplication was used).
    A Promise is returned when `callback` is not provided.

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)?** 
    -   `options.resolveWithObject` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** Resolve the Promise with an Object containing `data` and `info` properties instead of resolving only with `data`.
-   `callback` **[Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)?** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[Buffer](https://nodejs.org/api/buffer.html)>** when no callback is provided

## withMetadata

Include all metadata (EXIF, XMP, IPTC) from the input image in the output image.
The default behaviour, when `withMetadata` is not used, is to strip all metadata and convert to the device-independent sRGB colour space.
This will also convert to and add a web-friendly sRGB ICC profile.

**Parameters**

-   `withMetadata` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)?** 
    -   `withMetadata.orientation` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)?** value between 1 and 8, used to update the EXIF `Orientation` tag.


-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** Invalid parameters

Returns **Sharp** 

## jpeg

Use these JPEG options for output image.

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)?** output options
    -   `options.quality` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** quality, integer 1-100 (optional, default `80`)
    -   `options.progressive` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** use progressive (interlace) scan (optional, default `false`)
    -   `options.chromaSubsampling` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** set to '4:4:4' to prevent chroma subsampling when quality &lt;= 90 (optional, default `'4:2:0'`)
    -   `options.trellisQuantisation` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** apply trellis quantisation, requires mozjpeg (optional, default `false`)
    -   `options.overshootDeringing` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** apply overshoot deringing, requires mozjpeg (optional, default `false`)
    -   `options.optimiseScans` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** optimise progressive scans, forces progressive, requires mozjpeg (optional, default `false`)
    -   `options.optimizeScans` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** alternative spelling of optimiseScans (optional, default `false`)
    -   `options.force` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** force JPEG output, otherwise attempt to use input format (optional, default `true`)


-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** Invalid options

Returns **Sharp** 

## png

Use these PNG options for output image.

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)?** 
    -   `options.progressive` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** use progressive (interlace) scan (optional, default `false`)
    -   `options.compressionLevel` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** zlib compression level (optional, default `6`)
    -   `options.adaptiveFiltering` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** use adaptive row filtering (optional, default `true`)
    -   `options.force` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** force PNG output, otherwise attempt to use input format (optional, default `true`)


-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** Invalid options

Returns **Sharp** 

## webp

Use these WebP options for output image.

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)?** output options
    -   `options.quality` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** quality, integer 1-100 (optional, default `80`)
    -   `options.alphaQuality` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** quality of alpha layer, integer 0-100 (optional, default `100`)
    -   `options.lossless` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** use lossless compression mode (optional, default `false`)
    -   `options.nearLossless` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** use near_lossless compression mode (optional, default `false`)
    -   `options.force` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** force WebP output, otherwise attempt to use input format (optional, default `true`)


-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** Invalid options

Returns **Sharp** 

## tiff

Use these TIFF options for output image.

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)?** output options
    -   `options.quality` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** quality, integer 1-100 (optional, default `80`)
    -   `options.force` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** force TIFF output, otherwise attempt to use input format (optional, default `true`)
    -   `options.compression` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** compression options: lzw, deflate, jpeg (optional, default `'jpeg'`)
    -   `options.predictor` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** compression predictor options: none, horizontal, float (optional, default `'none'`)
    -   `options.squash` **[Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** squash 8-bit images down to 1 bit (optional, default `false`)


-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** Invalid options

Returns **Sharp** 

## raw

Force output to be raw, uncompressed uint8 pixel data.

Returns **Sharp** 

## toFormat

Force output to a given format.

**Parameters**

-   `format` **([String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object))** as a String or an Object with an 'id' attribute
-   `options` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** output options


-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** unsupported format or options

Returns **Sharp** 

## tile

Use tile-based deep zoom (image pyramid) output.
Set the format and options for tile images via the `toFormat`, `jpeg`, `png` or `webp` functions.
Use a `.zip` or `.szi` file extension with `toFile` to write to a compressed archive file format.

**Parameters**

-   `tile` **[Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)?** 
    -   `tile.size` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** tile size in pixels, a value between 1 and 8192. (optional, default `256`)
    -   `tile.overlap` **[Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** tile overlap in pixels, a value between 0 and 8192. (optional, default `0`)
    -   `tile.container` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** tile container, with value `fs` (filesystem) or `zip` (compressed file). (optional, default `'fs'`)
    -   `tile.layout` **[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** filesystem layout, possible values are `dz`, `zoomify` or `google`. (optional, default `'dz'`)

**Examples**

```javascript
sharp('input.tiff')
  .png()
  .tile({
    size: 512
  })
  .toFile('output.dz', function(err, info) {
    // output.dzi is the Deep Zoom XML definition
    // output_files contains 512x512 tiles grouped by zoom level
  });
```

-   Throws **[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)** Invalid parameters

Returns **Sharp** 