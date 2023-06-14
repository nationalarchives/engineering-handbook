# Accessibility

Accessibility means making sure your services can be used by the widest possible audience. Every time you send an email, prepare a presentation, write a post or a report you want as many people as possible to be able to understand it.

As a public body, we are under obligation to provide accessible services. From [understanding accessibility requirements for public sector bodies](https://www.gov.uk/guidance/accessibility-requirements-for-public-sector-websites-and-apps):

> All UK service providers have a legal obligation to make reasonable adjustments under the Equality Act 2010 or the Disability Discrimination Act 1995 (in Northern Ireland).
>
> ...
>
> If you created a new public sector website on or after 23 September 2018, you need to meet accessibility standards and should have published an accessibility statement. You need to review and update your statement regularly.

GOV.UK have published some helpful guidence on accessibility, such as:

- [Making your website or app accessible and publish an accessibility statement](https://www.gov.uk/guidance/make-your-website-or-app-accessible-and-publish-an-accessibility-statement)

## WCAG

The web content accessibility guidelines are a set of standards to ensure web-based content is as usable to as many people as possible.

It is broken down into four principles:

- Perceivable
- Operable
- Understandable
- Robust

You can read about the [four principles of accessibility](https://www.w3.org/WAI/WCAG21/Understanding/intro#understanding-the-four-principles-of-accessibility) from the WCAG guidelines published by W3C.

Each principle has a number of success criteria that have to be met. The full list can be found on the [Web Content Accessibility Guidelines (WCAG) 2.1
](https://www.w3.org/TR/WCAG21/) published by W3C.

Each criteria is given a level, either A, AA or AAA. A site meeting all the A criteria is the least accessible WCAG compliant site and one that meets all the A, AA and AAA criteria is the most accessible.

As of June 2023, WCAG 2.1 is the latest version of the guidelines. GOV.UK have published a guide on [understanding WCAG 2.1](https://www.gov.uk/service-manual/helping-people-to-use-your-service/understanding-wcag).

Our standard is to reach a minimum of **WCAG 2.1 AA**.

## Example accessibility checklist

To meet WCAG 2.1 to level AA you must be able to answer "yes" or "not applicable" to all of the following questions.

Answering "no" means that you are not meeting WCAG and your content will have barriers that will prevent some users from accessing it.

### Perceivable

1. Do all images have an appropriate text equivalent? Is essential visual information also available as text?
1. Do all audio files have a transcript? Is essential audio information available as text?
1. Do all videos have captions that are synchronised with the audio?
1. Does video that includes important visual information have an audio description?
1. Is all content structure that is communicated visually available to assistive technologies?
1. If styling is removed is the content in a logical order?
1. Have you avoided using visual characteristics to communicate information?
1. Have you avoided using colour as the only way to convey some information?
1. Can users stop audio that auto plays?
1. Does all text have sufficient contrast against the background colour?
1. Is the content fully usable when text is enlarged up to 200%?
1. Have you avoided using images of text?
1. Can users flip the content horizontally and vertically?
1. Have you added HTML autocomplete tokens to any forms collecting information about the user?
1. Does the page content resize to a single column with no horizontal and vertical scrolling?
1. Do all important graphical objects, interface components, and states have a colour contrast of 3:1?
1. Can line height, spacing between paragraphs and letter and word spacing be changed without breaking anything?
1. Where extra content is shown or hidden on focus, can it be dismissed, interacted with (and not disappear when the user moves to it) and will stay visible until dismissed by the user?

### Operable

1. Can all menus, links, buttons, and other controls be operated by keyboard?
1. Do pages that have time limits include mechanisms for adjusting those limits?
1. Can any content that moves or auto updates be stopped?
1. Have you avoided using content that flashes or flickers?
1. Can blocks of links and other interactive elements be bypassed by keyboard users?
1. Does each page have a unique title that indicates its purpose and context?
1. When using a keyboard to move through a page does the order make sense?
1. Is the purpose of every link clear from its link text?
1. Does the website have two or more ways of finding content, such as a navigation menu, search feature, or site map?
1. Are headings and labels clear and descriptive?
1. When using a keyboard to move through a page can you tell where you are?
1. Do you have shortcuts triggered by only one letter or character? If so can they be turned off or remapped by the user?
1. Does some of your site functionality need several fingers or complex gestures to operate it?
1. Does some of your site functionality work using a single point (e.g fingertip) and is it triggered the moment it is touched?
1. On forms and other components is the accessible name or label the same as any on-screen text?
1. Does your site respond to motion or movement to operate parts?

### Understandable

1. Has the language of the web page or document (or individual parts of a multilingual document) been defined?
1. Have you avoided links, controls, or form fields that automatically trigger a change in context?
1. Does the website include consistent navigation?
1. Are features with the same functionality labelled consistently?
1. Do forms provide helpful, understandable error and verification messages?

### Robust

1. Is the web page coded using valid HTML?
1. Do all interactive components have an accessible name and role, and when required state? Has the correct ARIA markup been used and does it validate?
1. Are status messages and updates given appropriate roles that can be understood by assistive technologies, without receiving focus?

## More (TODO)

- Best practices
- Testing requirements
- Supported assistive technologies
- Progressive enhancement
- https://gds.blog.gov.uk/2018/07/16/why-gov-uk-content-should-be-published-in-html-and-not-pdf/
