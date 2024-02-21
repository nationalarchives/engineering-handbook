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

Taking into consideration the [HTML standards](../technology/html.md), create markup that will accomplish the user need without requiring CSS or JavaScript.

Add the appropriate attributes to ensure the HTML meets [accessibility standards](accessibility.md).

### 2. Embellish with CSS

Add some styling in accordance with the [CSS standards](../technology/css.md) to enhance the component.

CSS shouldn't dictate the markup, although if you need more elements to achieve the style you need then add some extra HTML that you can hook into. Ensure the extra elements don't negatively affect the HTML-only solution.

Check your styles across all our [supported browsers](browser-support.md) as CSS support can vary wildly.

Use [caniuse.com](https://caniuse.com/) to check support for CSS features.

### 3. Elaborate with JavaScript

Use the [JavaScript standards](../technology/javascript.md) and add scripts which allow easier functionality.

You can use JavaScript to add more features as long as the user can complete their action without the need for JavaScript. An example would be to use JavaScript to open and close a menu. The menu should be visible to all but JavaScript would allow you to collapse it and save some screen real estate.

Avoid adding elements to the HTML that only JavaScript will find useful. If you need an extra button in order to perform an action and that button doesn't have a purpose without JavaScript, add the button element with JavaScript. This will avoid having "dead" components in the HTML.

As with CSS, you can use [caniuse.com](https://caniuse.com/) to check support for JavaScript features and APIs.

Don't forget to check the scenario where you have JavaScript available but no CSS.

### Case study: Tabs component

The [TNA tabs component](https://nationalarchives.github.io/tna-frontend/?path=/docs/components-tabs--docs) is an example of progressive enhancement.

#### HTML

Underneath the component is a simple set of anchors which link to elements with a unique ID.

This allows an HTML-only user to simply "jump" to each section.

```html
<a href="#unique-id-a">Alpha section</a>
<a href="#unique-id-b">Beta section</a>
<a href="#unique-id-c">Gamma section</a>

<section id="unique-id-a">
  <h2>Alpha title</h2>
  <p>Lorem ipsum</p>
</section>

<section id="unique-id-b">
  <h2>Beta title</h2>
  <p>Lorem ipsum</p>
</section>

<section id="unique-id-c">
  <h2>Gamma title</h2>
  <p>Lorem ipsum</p>
</section>
```

#### CSS

Adding CSS allowed us to make the anchors prettier and show/hide the sections using the CSS `:target` selector.

The scenario with CSS but no JavaScript is not ideal as the tabs don't yet have any helpful attributes to aid accessibility as they are simply `<section>` elements that are shown and hidden with CSS. The tabs are not marked up to be properly described.

This state is why the tab component still needs some work.

#### JavaScript

When JavaScript is available, we replace the anchors with `<button>` elements.

We then add click event listeners on the buttons in order to switch classes on both the buttons themselves as well as the sections. Then we use JavaScript to add the appropriate `aria-` attributes to the buttons and sections.

On switching tabs, we use JavaScript to update the `tabindex` and `hidden` attributes which allows users to more easily tab from the tab button to the open section.

## Single page applications

**React (along with other JavaScript libraries such as Vue and Angular) should not be used for any new National Archives applications.**

Designed as a SPA JavaScript library, React on its own doesn't fulfill our need for progressive enhancement. While it can be paired with frameworks like Next.js to provide SSR, many government departments have stopped using React and moved to more traditional technologies such as Python in order to provide better services.

GOV.UK stopped suggesting React and the repository that offered [GOV.UK React components](https://github.com/surevine/govuk-react-jsx) is no longer maintained.
