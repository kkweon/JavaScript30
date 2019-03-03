# CSS Variables

[Click for DEMO](https://kkweon.github.io/JavaScript30/03%20-%20CSS%20Variables/index.html)

## Define in the `:root`

```css
:root {
  --base: #ffc600;
  --spacing: 10px;
  --blur: 10px;
}
```

You can change in JavaScript using the following snippet

```js
document.documentElement.style.setProperty(`--base`, `#fff`);
```

## Use `data-` attribute to append units

```html
<input id="blur"
       type="range"
       name="blur"
       min="0"
       max="25"
       value="10"
       data-sizing="px">
```

By doing so, I can simply do

```js
document.documentElement.style.setProperty(
  `--${this.name}`,
  `${this.value}${suffix || ""}`
);
```
