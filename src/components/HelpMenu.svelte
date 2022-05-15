<script>
  import {
    Nav,
    NavItem,
    NavLink,
  } from "sveltestrap";

  import { push } from "svelte-spa-router";

  const linkEditor = "/";
  const linkHelp = "/help";
  const linkAbout = "/about";
</script>

<div class="nav-bar">
  <Nav dark>
    <!-- Navitems -->
    <NavItem>
      <NavLink on:click={() => push(linkEditor)}>Editor</NavLink>
    </NavItem>
    <NavItem>
      <NavLink on:click={() => push(linkHelp)}>Help</NavLink>
    </NavItem>
    <NavItem>
      <NavLink on:click={() => push(linkAbout)}>About</NavLink>
    </NavItem>
  </Nav>
</div>

<style>
  .nav-bar {
    background: linear-gradient(#2b2b2d, #47474a);
    /* background-color: rgb(65, 5, 5); */
    height: 50px;
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    font-size: large;
  }
</style>
