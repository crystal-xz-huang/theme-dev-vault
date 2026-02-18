#### Base64 Encode @font-face

Base64 is a binary-to-text encoding scheme that represents binary data in an ASCII string format. Data URI is just a URI scheme that provides a way to include data in-line. Basically, you’re converting the font file into a crazy long string of text that you can paste in to your css file.


Data URLs are of this format:

```html
data:[<media-type>][;base64],<data>
```

- `data:` – The scheme of the URL.

- `<media-type>` – An optional [MIME type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/MIME_types) (i.e. media type) such as `image/jpeg` for a JPEG image file. If omitted, defaults to `text/plain;charset=US-ASCII`. 

- `;base64` – that the data should be base64-decoded.

- `<data>` – The base64-encoded binary data.

## Font MIME Types

**Font/typeface data.** [(See font type registry at IANA)](https://www.iana.org/assignments/media-types/media-types.xhtml#font)

| Extension | Format                 | Document Type                   | MIME Type    | Notes                                                                                    |
| --------- | ---------------------- | ------------------------------- | ------------ | ---------------------------------------------------------------------------------------- |
| `.otf`    | OpenType               | OpenType Layout (OTF) Font Type | `font/otf`   |                                                                                          |
| `.ttf`    | TrueType               | TTF Font Type                   | `font/ttf`   |                                                                                          |
| `.woff`   | Web Open Font Format   | Web Open Font Format (WOFF)     | `font/woff`  | The existing registration "application/font-woff" is deprecated in favor of "font/woff". |
| `.woff2`  | Web Open Font Format 2 | Web Open Font Format (WOFF)     | `font/woff2` |                                                                                          |

## @font-face

```css
/*
Source - https://stackoverflow.com/a/79801768
Posted by MWMoriarty
Retrieved 2026-02-13, License - CC BY-SA 4.0
*/

@font-face {
  font-family: 'YourFontName';
  src: url(data:font/woff2;base64,d09GMgABAAAAA...) format('woff2');
  font-weight: normal;
  font-style: normal;
  font-display: swap; /* Best practice to prevent a flash of invisible text */
}
```

`font-display: swap`; This CSS property tells the browser to immediately display text with a fallback font while the custom font loads. This prevents the "flash of invisible text" (FOIT) and improves perceived performance.

## Encoding data into base64 format

Base64 encoding of a file or string on Linux and macOS systems can be achieved using the command-line `base64` tool:

```

```


# References

https://datatracker.ietf.org/doc/html/rfc8081#section-4.4.4

 
