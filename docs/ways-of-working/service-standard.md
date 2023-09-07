# Service standard

- Alignment to GDS Service Manual
- [The GDS Way](https://gds-way.cloudapps.digital/)
- https://www.gov.uk/guidance/the-technology-code-of-practice
- Twelve-factor methodology
- https://roca-style.org/

## Progressive enhancement

HTML-only users should be treated as first class citizens.

In acknowledgement of the web's inherent variability this development guide describes an approach based on the principle of progressive enhancement. This approach is in line with Service Manual guidance. In practice this means building the interface of a website or application in layers:

- If the user's browser only supports HTML they get content and the abilities to navigate and interact using forms
- If the user's browser also supports CSS the application looks better
- If it can run JavaScript (and/or supports newer technologies colloquially known as HTML5 and ESNext) the experience will be enhanced by those capabilities

The important points for developers to recognise are that:

- only the core HTML is required to meet users' basic needs, and;
- CSS, JavaScript and HTML5 APIs should be applied in such a way that they do not 'break' the experience for those clients that cannot support them

### Single page applications

React (along with other JavaScript libraries such as Vue and Angular) should not be used for any new National Archives applications.

Designed as a SPA JavaScript library, React on its own doesn't fulfill our need for progressive enhancement. While it can be paired with frameworks like Next.js to provide SSR, many government departments have stopped using React and moved to more traditional technologies such as Python in order to provide better services.

GOV.UK stopped suggesting React and the repository that offered [GOV.UK React components](https://github.com/surevine/govuk-react-jsx) is no longer maintained.
