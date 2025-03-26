# URLs

URLs and URIs in TNA services MUST:

1. be clear, unambiguous, easy to read, easy to type and easy to share
1. be in lower case
1. align with the title of the page
1. use words and should not contain acronyms, unless very well known or a department acronym (e.g. HMRC)
1. separate words with dashes (`-`) rather than underscores (`_`) so they are easy to read
1. use [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format if including a date

In addition, URLs and URIs in TNA services SHOULD:

1. not use a, an, the and other superfluous words (e.g. `/press-room/` rather than `/the-press-room/`)
1. use the verb stem where possible (e.g. `/find/` rather than `/finding/`)
1. not redirect a user to non-government sites
1. be based on user need rather than the name of a policy, scheme or service, which might change
1. include the year when using a short URL for one-off promotion of an annual event such as `/events/summer-camp-2020/`
1. have trailing slashes
1. have valid pages at every level of the URL (see [Valid URL parts](#valid-url-parts))

See [URL standards for GOV.UK](https://www.gov.uk/guidance/content-design/url-standards-for-gov-uk) for a more comprehensive list.

## Valid URL parts

An example of a confusing URL: `/catalogue/ref/E/190/558/15/`

This URL implies the following paths should also be valid which is probably not the case:

- `/catalogue/ref/E/190/558/`
- `/catalogue/ref/E/190/`
- `/catalogue/ref/E/`
- `/catalogue/ref/`

A better approach here could be: `/catalogue/?ref=E/190/558/15` as `/catalogue/` is very likely a valid page.

## Resources

- [Cool URIs don't change](https://www.w3.org/Provider/Style/URI) from w3.org
