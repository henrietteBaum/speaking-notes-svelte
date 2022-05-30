<script>
  import { marked } from "marked";
  import { NavItem, NavLink } from "sveltestrap";
  import EditorMenu from "./EditorMenu.svelte";
  import DdSpeak from "./DdSpeak.svelte";
  import { textStore } from "../stores/TextStores.js";
  let preview = false;

  function handleTogglePreview() {
    preview = !preview;
  }

  let visibleHelp = false;
  export const showHelp = () => {
    visibleHelp = !visibleHelp;
  };
</script>

<div class="div-menu">
  <EditorMenu />
  <DdSpeak {$textStore} />
  {#if preview}
    <NavItem>
      <NavLink on:click={handleTogglePreview} href="#">Editor</NavLink>
    </NavItem>
  {:else}
    <NavItem>
      <NavLink on:click={handleTogglePreview} href="#">Preview</NavLink>
    </NavItem>
  {/if}
</div>

<section>
  {#if preview}
    Preview
    <div class="prev">
      {@html marked($textStore)}
    </div>
  {:else}
    <textarea class="md-input" bind:value={$textStore} />
  {/if}
</section>

<!-- <Speech {mdText} /> -->
<style>
  .div-menu {
    background: linear-gradient(#390101, #7f0408);
    height: 50px;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    font-size: large;
    min-width: 700px;
  }

  .md-input {
    width: 100%;
    height: 100vh;
    background-color: rgb(50, 51, 59);
    color: white;
    border: none;
    outline: none;
    padding: 2em;
    font-size: larger;
    letter-spacing: 1px;
  }

  .prev {
    width: 100%;
    height: 100vh;
    background-color: rgb(86, 1, 1);
    color: white;
    text-align: left;
    padding: 1em;
  }

  section {
    background-color: rgb(50, 51, 59);
    color: orange;
    letter-spacing: 2px;
  }

  :global(li.nav-item) {
    list-style: none;
  }
</style>
