# Service standard

- Alignment to GDS Service Manual
- The GDS way
- Twelve-factor methodology

## Progressive enhancement

In acknowledgement of the web's inherent variability this development guide describes an approach based on the principle of progressive enhancement. This approach is in line with Service Manual guidance. In practice this means building the interface of a website or application in layers:

- If the user's browser only supports HTML they get content and the abilities to navigate and interact using forms.
- If the user's browser also supports CSS the application looks better.
- If it can run JavaScript (and/or supports newer technologies colloquially known as HTML5 and ESNext) the experience will be enhanced by those capabilities.

The important points for developers to recognise are that:

- only the core HTML is required to meet users' basic needs, and;
- CSS, JavaScript and HTML5 APIs should be applied in such a way that they do not 'break' the experience for those clients that cannot support them.
