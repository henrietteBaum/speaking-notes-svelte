<script>
  import {
    Nav,
    NavItem,
    NavLink,
    NavbarBrand
  } from "sveltestrap";

  import { push } from "svelte-spa-router";

  const linkEditor = "/";
  const linkHelp = "/help";
  const linkAbout = "/about";
</script>

<div class="nav-bar">
  <Nav dark>
    <!-- Navitems -->
    <NavbarBrand href="/">
      <img src="./sveltelogo.png" alt="svelte-logo" />
    </NavbarBrand>
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

  img {
    height: 20px;
    padding-left: 1em;
  }
</style>
