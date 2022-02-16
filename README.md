# introduce

Popup components，Support pop-up from top to bottom, left and right

[demo page](https://hengshanmwc.github.io/svelte-popup/dist/index.html)

# install

```
npm i svelte-popup
// or
yarn add svelte-popup
// or
pnpm i svelte-popup
```

# Basic use

```js
<script lang="ts">
  import { Popup } from "svelte-popup"; // 4kb
  let show = true
  function toggle() {
    show = !show;
  }
</script>
<main>
  <button on:click={toggle}>center:{show ? "hide" : "show"}</button>
  <Popup show={show} on:change={toggle}>
    <div class="center box">popup</div>
  </Popup>
</main>
```

# Prop

| name     |                       explain |                   type                   | default |
| -------- | ----------------------------: | :--------------------------------------: | :-----: |
| show     |                   show or not |                 boolean                  |    -    |
| position |               eject direction | center \| top \| right \| bottom \| left | center  |
| duration | transition attribute duration |                  number                  |   300   |
| delay    |    transition attribute delay |                  number                  |    0    |

# slot

| name | explain |
| ---- | ------: |
| -    | content |
