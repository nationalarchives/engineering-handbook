# Progressive enhancement

In acknowledgement of the web's inherent variability this development guide describes an approach based on the principle of progressive enhancement. This approach is in line with Service Manual guidance. In practice this means building the interface of a website or application in layers:

- If the user's browser only supports HTML they get content and the abilities to navigate and interact using forms
- If the user's browser also supports CSS the application looks better
- If it can run JavaScript (and/or supports newer technologies colloquially known as HTML5 and ESNext) the experience will be enhanced by those capabilities

The important points for engineers to recognise are that:

- only the core HTML is required to meet users' basic needs, and;
- CSS, JavaScript and HTML5 APIs should be applied in such a way that they do not 'break' the experience for those clients that cannot support them

Remember, [not everyone has JavaScript](https://www.kryogenix.org/code/browser/everyonehasjs.html).

## Approach and best practices

### 1. Start with the HTML

Taking into consideration the [HTML standards](../technology/frontend/html.md), create markup that will accomplish the user need without requiring CSS or JavaScript.

Add the appropriate attributes to ensure the HTML meets [accessibility standards](../technology/standards/accessibility.md).

### 2. Embellish with CSS

Add some styling in accordance with the [CSS standards](../technology/frontend//css.md) to enhance the component.

CSS shouldn't dictate the markup, although if you need more elements to achieve the style you need then add some extra HTML that you can hook into. Ensure the extra elements don't negatively affect the HTML-only solution.

Check your styles across all our [supported browsers](../technology/standards/browser-support.md) as CSS support can vary wildly.

Use [caniuse.com](https://caniuse.com/) to check support for CSS features.

### 3. Elaborate with JavaScript

Use the [JavaScript standards](../technology/frontend/javascript.md) and add scripts which allow easier functionality.

You can use JavaScript to add more features as long as the user can complete their action without the need for JavaScript. An example would be to use JavaScript to open and close a menu. The menu should be visible to all but JavaScript would allow you to collapse it and save some screen real estate.

Avoid adding elements to the HTML that only JavaScript will find useful. If you need an extra button in order to perform an action and that button doesn't have a purpose without JavaScript then consider either:

- adding the button element with JavaScript at runtime
- adding the button to the HTML with a `hidden` attribute and then remove the attribute as you run your JavaScript

This will avoid having "dead" components in the HTML.

As with CSS, you can use [caniuse.com](https://caniuse.com/) to check support for JavaScript features and APIs.

Don't forget to check the scenario where you have JavaScript available but no CSS.

## Single page applications

**React (along with other JavaScript libraries such as Vue and Angular) must not be used for any new National Archives applications.**

Designed as a SPA JavaScript library, React on its own doesn't fulfill our need for progressive enhancement. While it can be paired with frameworks like Next.js to provide SSR, many government departments have stopped using React and moved to more traditional technologies such as Python in order to provide better services.

GOV.UK stopped suggesting React and the repository that offered [GOV.UK React components](https://github.com/surevine/govuk-react-jsx) is no longer maintained.
