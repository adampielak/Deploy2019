#### Download predefined template
```bash
npx degit sveltejs/template <new project name>
```
#### Install required NPM packages
```bash
cd <created folder>
npm install
```
#### Run Svelte in development mode
```bash
npm run dev
```
#### Svelte context
App.svelte
```svelte
<script>
  import { onMount } from "svelte";
  import { getContext } from "svelte";
  import C1 from "./C1.svelte";

  onMount(_ => {
    let x = getContext("K1");
    console.log("xmount:", x);
  });
</script>

<C1 />
```
C1.svelte
```svelte
<script>
  import { onMount } from "svelte";
  import { setContext } from "svelte";

  onMount(() => {
    setContext("K1", { number: 19 });
  });
</script>

<h4>Context not available w/o C1 in DOM.</h4>
```
#### Svelte store
store.js
```svelte
import { writable } from 'svelte/store';

function createQuantity() {
  const { subscribe, set, update } = writable(100);

  return {
    subscribe,
    increment: () => update(n => n + 1)
  };
}

export const quantity = createQuantity();

quantity.subscribe(newValue => {
  console.log('quantity in store:', newValue);
});
```
App.svelte
```svelte
<script>
  import { quantity } from "./stores.js";

  console.log("store:", $quantity);
</script>

<h4>q = {$quantity}</h4>
<button on:click={quantity.increment}>+</button>
```

#### Resources
```html
https://www.toptal.com/front-end/svelte-framework-guide?utm_campaign=Svelte%20Status&utm_medium=email&utm_source=Revue%20newsletter
https://css-tricks.com/what-i-like-about-writing-styles-with-svelte/?utm_campaign=Svelte%20Status&utm_medium=email&utm_source=Revue%20newsletter
https://www.freecodecamp.org/news/the-svelte-handbook/?utm_campaign=Svelte%20Status&utm_medium=email&utm_source=Revue%20newsletter
http://www.sveltestatus.com/issues/the-svelte-handbook-a-common-log-in-form-in-svelte-svelte-commerce-more-204457
https://objectcomputing.com/resources/publications/sett/july-2019-web-dev-simplified-with-svelte
```
