# HTML

1. **Approach**
    1. HTML-only users MUST be treated as [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) ([Service standard - Progressive enhancement](../../ways-of-working/progressive-enhancement.md))
1. **Style**
    1. All HTML for National Archive applications MUST adhere to the [HTML5 standard](https://www.w3.org/TR/2011/WD-html5-20110405/)
    1. The `<html>` element SHOULD have a `lang` attribute
    1. The `lang` attribute on the `<html>` element SHOULD be `en`
    1. The `<title>` element SHOULD either follow the pattern `[page] - [service] - The National Archives` or `[page] - The National Archives`
    1. All tags MUST be closed, even where HTML5 might allow them not to be (as is the case for `<li>` and `<p>` tags)
    1. Full attribute syntax MUST be used and all attributes quoted (see the W3C description of [quoted attribute syntax](https://html.spec.whatwg.org/multipage/syntax.html#syntax-attributes))
    1. All tag names and attributes MUST be written in in lower case
    1. HTML SHOULD be properly indented to reflect its structure
    1. [Optional tags](https://html.spec.whatwg.org/multipage/syntax.html#optional-tags) MUST be used
1. **Accessibility**
    1. Services MUST follow the [TNA Accessibility standards](../standards/accessibility.md)

## Images

Acceptable file formats for images are:

| Format | Extention | MIME type       | Purpose                                                     |
| ------ | --------- | --------------- | ----------------------------------------------------------- |
| JPEG   | `.jpg`    | `image/jpeg`    | General purpose images                                      |
| WebP   | `.webp`   | `image/webp`    | General purpose images                                      |
| PNG    | `.png`    | `image/png`     | Images requiring lossless-ness or transparency (prefer SVG) |
| SVG    | `.svg`    | `image/svg+xml` | Logos, icons and fonts                                      |

### WebP

- WebP images MUST be served with a JPEG fallback

### SVGs

- Embedded SVGs MUST be made as accessible as possible (see [CSS Tricks - Accessible SVGs
](https://css-tricks.com/accessible-svgs/) for more details)

## Videos

Acceptable file formats for videos are:

| Format | Extention | MIME type    |
| ------ | --------- | ------------ |
| MP4    | `.mp4`    | `video/mp4`  |
| WebM   | `.webm`   | `video/webm` |

To use embedded media, refer to [YouTube](../../third-party/youtube.md).

### Player

Use [video.js](https://videojs.com/) as a video player for videos hosted by TNA as well as an overlay for YouTube videos.

See [`ds-frontend`](https://github.com/nationalarchives/ds-frontend/blob/main/src/scripts/media.js) for an example implimentation of video.js.
