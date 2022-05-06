<script>
  import { marked } from "marked";
  import { NavItem, NavLink} from "sveltestrap"
  import EditorMenu from "./EditorMenu.svelte"
  let mdText = "";
  let preview = false;

  function handleTogglePreview() {
    preview = !preview;
  }
</script>

<div class="div-menu">
{#if preview}
  <NavItem>
    <NavLink on:click={handleTogglePreview} href="#">Editor</NavLink>  
  </NavItem>
  {:else}
  <NavItem>
    <NavLink on:click={handleTogglePreview} href="#">Preview</NavLink>
  </NavItem>
  {/if}
<EditorMenu />
</div>

<section>
  {#if preview}
  Preview
  <div class="prev">
    {@html marked(mdText)} 
  </div>
  {:else}
  <textarea class="md-input" bind:value={mdText} />
  {/if}
</section>



<style>
  .div-menu {
    display: flex;
    flex-direction: row;
    width: 100%;
  }

  button {
    width: 5em;
    height: 2em;
    padding: auto;    
    background-color: rgb(65, 5, 5);
    color: orange;
    border: none;
  }
  .md-input {
    width: 100%;
    height: 100vh;
    background-color: rgb(50, 51, 59);
    color: white;
    border: none;
  }
  .prev {
    width: 100%;
    height: 100vh;
    background-color: rgb(86, 1, 1);
    color: white;
  }
</style>