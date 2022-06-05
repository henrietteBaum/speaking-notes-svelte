<script>
  import Router from "svelte-spa-router";
  import Editor from "./components/Editor.svelte";
  import Help from "./components/Help.svelte";
  import About from "./components/About.svelte";

  let routes = {
    "/": Editor,
    "/help": Help,
    "/about": About
  };
</script>

<main>
  <Router {routes} />
</main>

<style>
  main {
    text-align: center;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
