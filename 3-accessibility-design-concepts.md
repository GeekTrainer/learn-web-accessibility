Accessibility is a relatively large topic, and not one we can cover completely in a single Learn module. However, there are some of core tenets you will want to implement in every page you create. Designing an accessible page from the start is *always* easier than going back to an existing page to make it accessible.

## Using HTML the way it was designed

HTML provides numerous elements you can use to create a page, including buttons, links, and form controls. Each one of those elements has a set of built-in functionality, like being clickable, linkable, or accepting focus.

> ![NOTE]
> Focus is a web development term meaning a control is able to accept input from a keyboard. A button can accept focus, allowing someone to activate or "click" it by pressing the space bar.

With CSS and JavaScript it's possible to make any element look like any type of control. `<span>` could be used to create a `<button>`, and `<b>` could become `<a>`. While this may provide some shortcuts for styling or laying out your page, it removes the built-in functionality. Tools like a screen reader will not be able to understand a `<span>` is being used as a `<a>`. Someone navigating with a keyboard won't be able to set focus on a `<div>` element which has been programmed to simulate a `<button>`.

Another HTML element frequently skipped is headers (`<h1>` through `<h6>`). From a visual standpoint, header tags start from largest to smallest text size. This leads many developers to forgo header elements and instead stylize `<div>` or other generic elements. Unfortunately stylized generic elements only convey visual information rather than structural. Screen reader users [rely heavily on headings](https://webaim.org/projects/screenreadersurvey8/#finding) to find information and navigate through a page. Writing descriptive heading content and using semantic heading tags are important for creating an easily navigable site for screen reader users.

As a best practice, you should always use the appropriate HTML when creating controls on a page. If you want a hyperlink, use `<a>`, or a `<button>` for a button.

## Use good visual clues

Developers often think about screen readers as the only accessibility tool. However, there are numerous other tools one might use, or may not even use a tool at all. Users who are using the browser will rely on certain visual cues to understand how to interact with your page.

One of the great features of CSS is it provides complete control over how to display a page, including removing certain display elements. This includes removing the outline from a textbox, or the underline from a hyperlink. Unfortunately, removing those types of cues can make it more challenging for someone who depends on them to recognize the type of control.

## The importance of link text

Hyperlinks are core to navigating the web, so much so it's the first word in the abbreviation for HTML (HyperText Markup Language). As a result, ensuring a screen reader can properly read links allows all users to navigate your site.

Consider the two links below:

- The little penguin, sometimes known as the fairy penguin, is the smallest penguin in the world. [Click here](https://en.wikipedia.org/wiki/Little_penguin) for more information.
- The little penguin, sometimes known as the fairy penguin, is the smallest penguin in the world. Visit https://en.wikipedia.org/wiki/Little_penguin for more information.

> ![IMPORTANT]
> The two examples demonstrate what you should *not* use as a web developer

While these may appear to be perfectly fine for someone with full sight, they won't work as you might expect with a screen reader. Remember, screen readers read the text. If a URL appears in the text, the screen reader will read the URL. Generally speaking, the URL does not convey meaningful information, and can sound annoying. You may have experienced this if your phone has ever audibly read a text message with a URL.

Screen readers also have the ability to read only the hyperlinks on a page, much in the same way a sighted person would scan a page for links. If the link text is always "click here", all the user will hear is "click here, click here, click here, click here, click here, ..." All links are now indistinguishable from one another, and is generally a frustrating experience.

The word *click* is also a problem, as not all users may click. Phone users will tap, keyboard users may press enter or space bar, and other clients will use other means.

We need to ensure we're always using meaningful link text. Good link text briefly describes what's on the other side of the link. In the above example talking about little penguins, the link is to the Wikipedia page about the species. The phrase *little penguins* would make for perfect link text as it makes it clear what someone will learn about if they click the link - little penguins.

- The [little penguin](https://en.wikipedia.org/wiki/Little_penguin), sometimes known as the fairy penguin, is the smallest penguin in the world.

> ![NOTE]
> As an added bonus for ensuring your site is accessible to all, you'll help search engines navigate your site as well. Search engines use link text to learn the topics of pages. So using good link text helps everyone!

## Accessible Rich Internet Applications (ARIA)

Imagine the following product page:

| Product      | Description        | Order        |
| ------------ | ------------------ | ------------ |
| Widget       | [Description]('#') | [Order]('#') |
| Super widget | [Description]('#') | [Order]('#') |

This is a pretty common layout for a page showing information about various items in a table, with links to the description and order. Duplicating the text of description and order make sense for someone using a browser. However, someone using a screen reader would only hear the words *description* and *order* repeated without context.

To support these types of scenarios, HTML supports a set of attributes known as [Accessible Rich Internet Applications (ARIA)](https://developer.mozilla.org/docs/Web/Accessibility/ARIA). These attributes allow you to provide additional information to screen readers. For links, you can use `aria-label` to describe the link when the format of the page doesn't allow you to. The description for widget could be set as:

``` html
<a href="#" aria-label="Widget description">description</a>
```

ARIA has numerous uses beyond adding text for screen readers to read for links. It can be used to describe the roles certain elements play when semantic HTML isn't available. When creating a tree for example, you can use ARIA roles to describe the interface to a screen reader.

```html
<h2 id="tree-label">File Viewer</h2>
<div role="tree" aria-labelledby="tree-label">
  <div role="treeitem" aria-expanded="false" tabindex="0">Uploads</div>
</div>
```

> ![IMPORTANT]
>
> However, using semantic markup and good link text as described earlier generally supersedes the use of ARIA. Browsers and screen readers are not the only clients a user may use, and designing your page to work well for all clients and users should be your primary goal.

## Images

It goes without saying screen readers are unable to automatically read what's in an image. Ensuring images are accessible doesn't take much work - it's what the `alt` attribute is all about. All meaningful images should have an `alt` to describe what they are or the information the image is trying to convey. Images that are purely decorative should have their `alt` attribute set to an empty string: `alt=""`; this prevents screen readers from unnecessarily announcing the decorative image.

> ![NOTE]
> As you might expect, search engines are also unable to understand what's in an image. They also use alt text. So once again, ensuring your page is accessible provides additional bonuses!

## The keyboard

Some users are unable to use a mouse or trackpad/touchpad, instead relying on keyboard interactions to tab from one element to the next. It's important for your pages to present your content in logical order so a keyboard user can access each interactive element as they move down a document.

When navigating a page using tab, focus will move from one control to the next based on the order the controls are listed in the HTML source. The controls for your page should be listed in the HTML source in which you expect the page to be navigated, while relying on CSS to layout the page visually to users.

For example, imagine creating a form with two columns. You will want to consider what the natural flow is for someone filling out the form, and list the controls in that order. Then you can use CSS to create the columns, and display the controls in their appropriate locations.

Keyboard navigation relies heavily on semantic HTML. Certain controls (like buttons) accept focus while `div` elements do not. If you are recreating controls which already exist in HTML you are making it more difficult for someone to use your page with a keyboard.

> ![IMPORTANT]
> Keyboard navigation needs to be tested manually, and should be done on every page you create. WebAIM has more information about [keyboard navigation strategies](https://webaim.org/techniques/keyboard/).
