# HTML

1. **Approach**
    1. HTML-only users MUST be treated as [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) ([Service standard - Progressive enhancement](../../ways-of-working/service-standard/#progressive-enhancement))
1. **Style**
    1. All HTML for National Archive applications MUST adhere to the [HTML5 standard](https://www.w3.org/TR/2011/WD-html5-20110405/)
    1. The `<html>` element SHOULD have a `lang` attribute
    1. The `lang` attribute on the `<html>` element SHOULD be `en-GB`
    1. The `lang` attribute on the `<html>` element COULD be `en`
    1. The `<title>` element SHOULD either follow the pattern `[page] - [service] - The National Archives` or `[page] - The National Archives`
    1. All tags MUST be closed, even where HTML5 might allow them not to be (as is the case for `<li>` and `<p>` tags)
    1. Full attribute syntax MUST be used and all attributes quoted (see the W3C description of [quoted attribute syntax](https://html.spec.whatwg.org/multipage/syntax.html#syntax-attributes))
    1. All tag names and attributes MUST be written in in lower case
    1. HTML SHOULD be properly indented to reflect its structure
    1. [Optional tags](https://html.spec.whatwg.org/multipage/syntax.html#optional-tags) MUST be used
1. **A11y**
    1. Appropriate semantic elements MUST be used (e.g. `<section>`, `<article>`, `<nav>`, `<aside>`)
    1. There MUST be one `<main>` element with a `role="main"` attribute applied for compatibility with older browsers
    1. The HTML outline MUST be logical and based on an appropriate, sequentially descending heading structure
    1. In-page navigation MUST be facilitated with "skip to content" and "back to top" links where appropriate

## Images

Acceptable file formats for images are:

| Format | Extention | MIME type       | Purpose                                                     |
| ------ | --------- | --------------- | ----------------------------------------------------------- |
| JPEG   | `.jpg`    | `image/jpeg`    | General purpose images                                      |
| WebP   | `.webp`   | `image/webp`    | General purpose images                                      |
| PNG    | `.png`    | `image/png`     | Images requiring lossless-ness or transparency (prefer SVG) |
| SVG    | `.svg`    | `image/svg+xml` | Logos, icons and fonts                                      |

### PNGs

- PNGs MUST be served with a JPEG fallback

### SVGs

- Embedded SVGs MUST be made as accessible as possible (see [CSS Tricks - Accessible SVGs
](https://css-tricks.com/accessible-svgs/) for more details)




## Videos

Acceptable file formats for videos are:

| Format | Extention | MIME type    |
| ------ | --------- | ------------ |
| MP4    | `.mp4`    | `video/mp4`  |
| WebM   | `.webm`   | `video/webm` |

To use embedded media, refer to [YouTube](../../third-party/youtube/).
