# CDNs

A CDN COULD be used to reduce server load and request resources from edge locations.

When using content from a CDN, you MUST use as many of the solutions as possible to keep your site secure from attacks:

1. [Use a reputable CDN provider](#providers)
1. [Use HTTPS](#https)
1. [Use a fixed version](#fixed-versions)
1. [Use an integrity string](#integrity-string)
1. [Impliment a CSP](#csp)

## Providers

The three CDN providers TNA considers reputable are:

- [jsDelivr](https://www.jsdelivr.com/)
- [unpkg](https://www.unpkg.com/)
- [CDNJS](https://cdnjs.com/)

## HTTPS

You MUST use HTTPS for loading any resources. This helps prevent against eavesdropping, data tampering, and man-in-the-middle attacks.

## Fixed versions

Use a specific version of the package (e.g. `0.1.42`) rather than `latest`. This should help protect against dependency confusion attacks.

## Integrity string

In addition to using a fixed version, add an [integrity](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script#integrity) hash to the resource. This is usually a SHA-256 hash of the resource which is provided by lots of CDNs.

This helps protect against man-in-the-middle attacks where the resource is switched for a malicious one. In this instance, the hash would not match your `integrity` attribute and the resource would fail to load.

[Support for subresource integrity](https://caniuse.com/subresource-integrity) is very good but can't be relied upon for older browsers.

An example of resources with a fixed version and integrity attribute:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@nationalarchives/frontend@0.1.42/nationalarchives/all.css"
  integrity="sha256-E9+MZSa1W0ac+Ko1Eje19/F2l09uG/hzzC/mDO00UHY="
  crossorigin="anonymous"
/>
<script
  src="https://cdn.jsdelivr.net/npm/@nationalarchives/frontend@0.1.42/nationalarchives/all.js"
  integrity="sha256-ZFpoR31xQI3LK43xmEk9t0RBYwwwJfRG0Lwey0Q2zro="
  crossorigin="anonymous"
></script>
```

## CSP

Do not use content from a CDN without [setting up a CSP](../technology/standards/security.md#csp) on the frontend of your service.
