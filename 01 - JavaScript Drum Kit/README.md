# Note

[Click for demo](https://kkweon.github.io/JavaScript30/01%20-%20JavaScript%20Drum%20Kit/)

## data-key attribute

If there is an element

```html
<div data-key="65"></div>
```

you can extract using `elem.dataset.key === "65"` (note type is `string`)


## transitionend

There is an event for CSS `transitionend`

## Add/Remove/Toggle Class

```js
elem.classList.add("playing")
elem.classList.remove("playing")
elem.classList.toggle("playing")
```

## Audio Element

```html
<audio data-key="76" src="sounds/tink.wav"></audio>
```

```js
audio.currentTime
audio.play()
```

## Full Code

```javascript
const divs = [...document.querySelectorAll(".key")];
const audios = [...document.querySelectorAll("audio")];

const key2audio = divs.reduce((dict, elem, idx) => {
  const keyCode = elem.dataset.key;
  dict[keyCode] = {
    elem: divs[idx],
    audio: audios[idx]
  };
  return dict;
}, {});

window.addEventListener("keydown", e => {
  if (e.keyCode in key2audio) {
    const { audio, elem } = key2audio[e.keyCode];
    elem.classList.add("playing");
    audio.currentTime = 0;
    audio.play();
  }
});

divs.forEach(div => {
  div.addEventListener("transitionend", e => {
      if (e.propertyName !== "transform") return
      e.currentTarget.classList.remove("playing")
  });
});
```
