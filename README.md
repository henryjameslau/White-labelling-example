# White-labelling-example
This is a proof of concept for white labelling intereactives or other SvelteKit products that use ONSvisual svelte-components.

There is custom stylesheet called `overrides.css` in the static folder. The vite.config.js has been edited so that the static folder is also served on localhost. To view the article with the custom style sheet being used visit

```
localhost:5173/?customStylesheet=http://localhost:5173/static/overrides.css
```

## How it works
When using the `<Theme>` component specify a `theme` and set the prop `allowClientOverrides` to true. This then sets a `div` with the class `client-css-override` inside the theme which can then be targetting with CSS, for example

```css
div.client-css-override{
    --text: #f9ea9a;
}
```

The external stylesheet is loaded if `customStylesheet` is passed as a parameter in the url. SvelteKit uses the `$page` store to get the URL and then gets the key `customStylesheet`.

```
const customStylesheet = $page.url.searchParams.get("customStylesheet");
```

If there is a customStylesheet it gets loaded via a `<link>` element.

```
{#if customStylesheet}
       <link rel="stylesheet" href={customStylesheet} />
{/if}
```