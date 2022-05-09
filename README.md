# Speaking Notes Svelte




## routing

Svelte-SPA-router

Routing in App.svelte:
```js
	<nav>
		<a href="/#/">Editor</a>
		<a href="/#/help">Help</a>
		<a href="/#/about">About</a>
	</nav> 
```
Instead of setting up a navigation in App.svelte I habe used **Sveltestrap** in a separate component `EditorMenu`, because I want to use the Dropdown from Sveltestrap.

For routing to Help and About I put a button inside my sveltestrap-Nav, which liks to the components. Found this example:

[Stackoverflow:](https://stackoverflow.com/questions/65649357/svelte-pass-useaction-to-component-child)

```svelte
<script>
  import { Button } from 'sveltestrap';
  import { push } from 'svelte-spa-router';
  let myLink = '/foo/bar';
</script>

<Button on:click={() => push(myLink)}>
  Click here
</Button>
```

And in my EditorMenu:

```html
<script>
  import { push } from "svelte-spa-router"

  const linkHelp = "/help";
  const linkAbout ="/about"; 
  </script>

<Nav>
<!-- ... -->
  <NavItem>
    <button on:click={() => push(linkHelp)}>Help</button>
  </NavItem>
  <NavItem>
    <button on:click={() => push(linkAbout)}>About</button>
  </NavItem>
<!-- ... -->
</Nav>
```

## Speech Synthesis

Use props and component for Speech-Synthesis

```svelte
// Speech.svelte

<script>
    export mdText
</script>
```

## Learning sources:

- https://stackoverflow.com/questions/65649357/svelte-pass-useaction-to-component-child

- [YouTube: Svelte and Speech-Synthesis-API](https://www.youtube.com/watch?v=XDdKWOqCcZk)
- [GitHub: phptuts](https://github.com/phptuts/speechsynthesissvelte)

- [YouTube: Codeevolution, Svelte components](https://www.youtube.com/watch?v=v943IElHCeY)

