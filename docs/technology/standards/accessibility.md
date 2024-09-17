# Accessibility

Accessibility means making sure your services can be used by the widest possible audience. Every time you send an email, prepare a presentation, write a post or a report you want as many people as possible to be able to understand it.

As a public body, we are under obligation to provide accessible services.

> All UK service providers have a legal obligation to make reasonable adjustments under the Equality Act 2010 or the Disability Discrimination Act 1995 (in Northern Ireland).
>
> If you created a new public sector website on or after 23 September 2018, you need to meet accessibility standards and should have published an accessibility statement. You need to review and update your statement regularly.
>
> — [Understanding accessibility requirements for public sector bodies](https://www.gov.uk/guidance/accessibility-requirements-for-public-sector-websites-and-apps) by GOV.UK

## Standards

1. **W3C WAI**
    1. All TNA services MUST meet a minimum standard of **[WCAG](#wcag) 2.2 AA**
    1. All TNA services that all users to author content SHOULD meet a minimum standard of [**ATAG 2.0 AA**](https://www.w3.org/WAI/standards-guidelines/atag/)
1. **Format**
    1. All TNA content MUST be available in [HTML format](../frontend/html.md)
    1. TNA content COULD also be offered in a [PDF format](#pdfs)
1. **HTML**
    1. Appropriate semantic elements MUST be used (e.g. `<section>`, `<article>`, `<nav>`, `<aside>`)
    1. There MUST be one `<main>` element
    1. The HTML outline MUST be logical and based on an appropriate, sequentially descending heading structure
    1. In-page navigation MUST be facilitated with "skip to content" and "back to top" links where appropriate (see [skip links in the National Archives Design System](https://nationalarchives.github.io/design-system/components/skip-link/))
1. **Audit**
    1. As a bare minimum, all pages on TNA services MUST pass an [axe](https://www.deque.com/axe/) test, a [WAVE](https://wave.webaim.org/) test and [Google's Lighthouse accessibility](https://developer.chrome.com/docs/lighthouse/accessibility/scoring) test
    1. New services MUST undergo an accessibility audit
    1. Services SHOULD undergo regular internal accessibility audits
    1. Services SHOULD undergo regular external accessibility audits

## WCAG

The Web Content Accessibility Guidelines (WCAG) are a set of standards to ensure web-based content is as usable to as many people as possible.

It is broken down into four principles:

- Perceivable
- Operable
- Understandable
- Robust

You can read about the [four principles of accessibility](https://www.w3.org/WAI/WCAG22/Understanding/intro#understanding-the-four-principles-of-accessibility) from the WCAG guidelines published by W3C.

Each principle has a number of success criteria that have to be met. The full list can be found on the [Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/WCAG22/) published by W3C.

Each criteria is given a level, either *A*, *AA* or *AAA*. A site meeting all the *A* criteria is the least accessible WCAG compliant site and one that meets all the *A*, *AA* and *AAA* criteria is the most accessible.

As of October 2023, WCAG 2.2 is the latest version of the guidelines. GOV.UK have published a guide on [understanding WCAG 2.2](https://www.gov.uk/service-manual/helping-people-to-use-your-service/understanding-wcag).

## Format

### PDFs

Avoid using PDFs where possible.

> Compared with HTML content, information published in a PDF is harder to find, use and maintain. More importantly, unless created with sufficient care PDFs can often be bad for accessibility and rarely comply with open standards.
>
> — [Why GOV.UK content should be published in HTML and not PDF](https://gds.blog.gov.uk/2018/07/16/why-gov-uk-content-should-be-published-in-html-and-not-pdf/) by GOV.UK

## Resources

### Other government departments
- [Making your website or app accessible and publish an accessibility statement](https://www.gov.uk/guidance/make-your-website-or-app-accessible-and-publish-an-accessibility-statement) by GOV.UK
- [Accessibility checklist](https://hmlr-design-system.herokuapp.com/accessibility/accessibility-checklist/) by HM Land Registry
- [DWP Accessibility Manual](https://accessibility-manual.dwp.gov.uk/)
- [Home Office Design System](https://design.homeoffice.gov.uk/accessibility)
- [NHS Service Manual](https://service-manual.nhs.uk/accessibility)
- [Intelligence Community Design System](https://design.sis.gov.uk/accessibility)

### External resources

- [Heading off confusion: When do headings fail WCAG?](https://www.tpgi.com/heading-off-confusion-when-do-headings-fail-wcag/)

## More (TODO)

- Best practices
- Testing requirements
- Supported assistive technologies
