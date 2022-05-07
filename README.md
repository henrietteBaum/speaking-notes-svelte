# Speaking Notes Svelte




## routing

Svelte-SPA-router

```javascript
<script>
  import { Button } from 'sveltestrap';
  import { push } from 'svelte-spa-router';
  let myLink = '/foo/bar';
</script>

<Button on:click={() => push(myLink)}>
  Click here
</Button>


```

## Learning sources:

https://stackoverflow.com/questions/65649357/svelte-pass-useaction-to-component-child

